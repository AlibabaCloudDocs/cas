---
keyword: [Alibaba Cloud SSL Certificates Service, NGINX server, Tengine server, HTTPS support]
---

# Install an SSL certificate on an NGINX or Tengine server

This topic describes how to download an SSL certificate from the Alibaba Cloud SSL Certificates Service console and install it on an NGINX or Tengine server.

A remote logon tool, such as PuTTY or Xshell, is available.

-   In this example, CentOS 8 and Nginx 1.14.1 are used. Operations for other versions of CentOS and NGINX may be slightly different.
-   In this example, the certificate name is **domain name**, the certificate file name is **domain name.pem**, and the key file name is **domain name.key**.
-   The following files can be extracted from a downloaded NGINX certificate package:
    -   .pem: the certificate file.
    -   .key: the key file. If you have not selected**Automatic** for CRS Generation when you apply for the certificate, the downloaded certificate package does not contain the .key file. You must manually create a key file.

**Note:** The **.pem** certificate file is a Base64-encoded text file. You can change its extension as needed. For more information about the certificate formats, see [What formats are used for mainstream digital certificates?](/intl.en-US/Product Introduction/SSL certificate concepts/What formats are used for mainstream digital certificates.md)

## Download and install the SSL certificate

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  In the left-side navigation pane, click **Overview**.

3.  On the SSL Certificates page, find the SSL certificate that you want to download and click **Download**.

4.  In the **Download Certificate** dialog box, find the certificate for **Nginx**, and click **Download** in the **Actions** column to download the certificate package to your computer.

5.  Decompress the certificate package.

    The following two files are extracted from the package:

    -   Certificate file \( a .pem file\)
    -   Key file \(a .key file\)
    ![Certificate and key files](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66002/156446766033690_en-US.png)

6.  Log on to your NGINX server. Run the following commands to go to the NGINX installation directory, which is /usr/local/nginx/conf by default, and create a directory named **cert**:

    ```
    cd /usr/local/nginx/conf  # Go to the NGINX installation directory. The default NGINX installation directory is used in this example. You can replace it with the actual installation directory.
    mkdir cert  # Create a cert directory.
    ```

7.  Use the file upload function of a remote logon tool, such as PuTTY or Xshell, to upload the certificate file and key file to the **cert** directory on the NGINX server.

    **Note:** If you have selected **Manual** for CSR Generation when you apply for the certificate, place the manually created key file in the **cert** directory and name the key file **domain name.key**.

8.  Run the following command to open the configuration file NGINX installation directory/conf/nginx.conf:

    ```
    vim /usr/local/nginx/conf/nginx.conf # Open the configuration file. The default directory of the NGINX configuration file is used in this example. You can replace it with the actual directory.
    ```

    Press **i** to enter the edit mode. Find the HTTP settings in the configuration file. Then, add the following server configuration or modify the server configuration if it already exists based on the comments:

    ```
    # Configuration items that start with ssl are related to certificate settings. You can configure other items based on your business requirements.
    server {
             listen 443 ssl; # Set the HTTPS port to 443. If the HTTPS port is not configured, NGINX may fail to start. If your NGINX version is 1.15.0 or later, use listen 443 ssl, instead of listen 443 and ssl on.
             server_name www.certificatestests.com; # Replace www.certificatestests.com with the domain name that is bound to your certificate, such as www.example.com. If your certificate applies to a wildcard domain name, enter a wildcard domain name, such as *.aliyun.com.
             root html;
             index index.html index.htm;
             ssl_certificate cert/domain name.pem;  # Replace domain name.pem with the name of your certificate file.
             ssl_certificate_key cert/domain name.key;  # Replace domain name.key with the name of your key file.
             ssl_session_timeout 5m;
             ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:! NULL:! aNULL:! MD5:! ADH:! RC4;  # Specify the cipher suite to use.
             ssl_protocols TLSv1 TLSv1.1 TLSv1.2;  # Specify the supported protocol versions.
             ssl_prefer_server_ciphers on;
             location / {
             root html;  # Specify the directory of your website.
             index index.html index.htm;
                        }
          }
    ```

    After you modify the configuration file, press **Esc**. Then, enter :wq! and press **Enter** to save the configuration file and exit the edit mode.

9.  Run the following commands to go to the **sbin** directory, which contains the NGINX executable file, and restart the NGINX service:

    ```
    cd /usr/local/nginx/sbin # Go to the **sbin** directory on the NGINX server.
    ./nginx -s reload  # Restart the NGINX server.
    ```

    **Note:**

    -   If `the "ssl" parameter requires ngx_http_ssl_module` error appears during the restart, recompile the NGINX program and add the `--with-http_ssl_module` setting when you install NGINX.
    -   If the `"/cert/3970497_pic.certificatestests.com.pem":BIO_new_file() failed (SSL: error:02001002:system library:fopen:No such file or directory:fopen('/cert/3970497_pic.certificatestests.com.pem','r') error:2006D080:BIO routines:BIO_new_file:no such file)` error appears during the restart, remove the forward slash \(`/`\) that precedes the relative path of the certificate file. For example, remove the forward slash \(`/`\) that precedes the relative path `/cert/3970497_pic.certificatestests.com.pem`. The correct relative path is `cert/3970497_pic.certificatestests.com.pem`.
10. Redirect HTTP requests to HTTPS.

    In the NGINX configuration file, add the following rewrite configuration item below the domain name of the HTTP website to redirect all HTTP requests to HTTPS:

    ```
    server {
     listen 443 ssl;
     server_name www.certificatestests.com; # Replace www.certificatestests.com with the domain name that is bound to your certificate, such as www.example.com.
    rewrite ^(.*)$ https://$host$1 permanent;  # Redirect all HTTP requests to HTTPS.
     location / {
    index index.html index.htm;
    }
    }
    ```


## Configure the SSL certificate on a virtual host

1.  Log on to your virtual host and create a **cert** directory in the Web directory. Then, copy the certificate file and key file to the **cert** directory.

2.  Open the configuration file vhost.conf or \*.conf on the virtual host. Add the following settings to the end of the configuration file based on the comments:

    ```
    server {
     listen 80;
     server_name localhost ;
     location / {
    index index.html index.htm;
    }
    server {
    listen 443 ssl;
    server_name localhost;
    root html;
    index index.html index.htm;
    ssl_certificate cert/domain name.pem;   # Replace domain name.pem with the name of your certificate file.
    ssl_certificate_key cert/domain name.key;   # Replace domain name.key with the name of your key file.
    ssl_session_timeout 5m;
    ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:! NULL:! aNULL:! MD5:! ADH:! RC4;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    ssl_prefer_server_ciphers on;
    location / {
    index index.html index.htm;
    }
    ```

3.  Save the vhost.conf file or the \*.conf file and exit.

4.  Redirect HTTP requests to HTTPS.

    Open the .htaccess file in the Web directory. If the file does not exist, create one. Add the following rewrite configuration item to redirect all HTTP requests to HTTPS:

    ```
    RewriteEngine On
    RewriteCond %{HTTP:From-Https} ! ^on$ [NC]
    RewriteCond %{HTTP_HOST} ^(www.)? yourdomain.com$ [NC]                # Replace yourdomain.com with the domain name that is bound to your SSL certificate, such as example.com.
    RewriteRule ^(.*)$ https://www.yourdomain.com/$1 [R=301,L]           # Replace yourdomain.com with the domain name that is bound to your SSL certificate, such as example.com.
    ```

5.  Restart the virtual host.


**Note:** After the certificate is installed, you must configure pseudo static rules on the virtual host. This way, the entire website supports HTTPS. Otherwise, only the homepage of your website supports HTTPS, and other directories do not.

## What to do next

After you complete certificate installation, you can verify it by accessing the domain name that is bound to the certificate.

```
https://domain name   # Replace domain name with the domain name that is bound to your certificate.
```

If a lock icon appears in the address bar, the certificate has been installed.

After a DV or OV SSL certificate is deployed on your server, the following results appear when you access the website from your browser:

![Browser display effect after a DV or OV SSL certificate is installed](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8346805061/p108043.png)

After an EV SSL certificate is deployed on your server, the following results appear when you access the website from your browser:

![Browser display effect after an EV SSL certificate is installed](../images/p108044.png)

If you encounter the following issues, handle them based on the following table.

|Issue|Possible cause|Solution|
|-----|--------------|--------|
|Your website cannot be accessed by using HTTPS.|Port 443 of the NGINX server on which you install the certificate is not enabled, or traffic to this port is blocked.|If your website is built on an Alibaba Cloud ECS instance, log on to the [ECS console](https://ecs.console.aliyun.com) and go to the **Security Groups** page. Then, configure security group rules to allow inbound traffic to the 443 port.|
|The "Your connection to this site is not fully secure" message is reported.|The code of your website uses HTTP.|Change the protocol from HTTP to HTTPS in the code of your website.**Note:** The implementation logic varies with the website code. Change the protocol based on your actual situation. |

## References

-   [Install an SSL certificate on a Tomcat server](/intl.en-US/Download and install SSL certificates/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md)
-   [Install SSL certificates on Apache servers](/intl.en-US/Download and install SSL certificates/Install SSL certificates on Apache servers.md)
-   [Deploy SSL certificate on Ubuntu Apache2](/intl.en-US/Best Practices/Deploy SSL certificate on Ubuntu Apache2.md)
-   [How do I deploy the issued certificate in Apache server]()
-   [Install SSL certificates in IIS servers](/intl.en-US/Download and install SSL certificates/Install SSL certificates in IIS servers.md)
-   [Deploy SSL certificates on CentOS-based Tomcat 8.5 or 9.0](/intl.en-US/Best Practices/Deploy SSL certificates on CentOS-based Tomcat 8.5 or 9.0.md)
-   [An SSL certificate is configured by the jetty server](/intl.en-US/Download and install SSL certificates/An SSL certificate is configured by the jetty server.md)

