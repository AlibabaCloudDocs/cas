---
keyword: [SSL Certificates Service, NGINX server, Tengine server, HTTPS support]
---

# Install an SSL certificate on an NGINX server or a Tengine server

You can purchase and issue a certificate in the SSL Certificates Service console and then download and install the certificate on an NGINX server or a Tengine server. This topic describes how to download and install the certificate.

-   The certificate is issued in the SSL Certificates Service console. For more information, see [Apply for a certificate](/intl.en-US/Issue Certificates/Apply for a certificate.md).
-   A remote logon tool, such as PuTTY or Xshell, is available for logging on to your web server.

In this example, CentOS 8 and NGINX 1.14.1 are used. Operations for other versions of CentOS and NGINX may be slightly different.

In this example, the certificate name is **cert-file-name**. Therefore, the Certificate Authority \(CA\) certificate file is named cert-file-name.pem, and the key file is named cert-file-name.key.

**Note:** In actual use, you must replace **cert-file-name** with the name of your certificate based on the description of the sample code. For more information about how to obtain a certificate name, see [Download a certificate to your on-premises machine](#step_g2p_wai_ral).

## Step 1: Download a certificate to your on-premises machine

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas)[SSL Certificates Service console](https://partners-intl.aliyun.com/#/cas).

2.  On the **Overview** page, select **Issued** from the status drop-down list above the certificate list.

    ![已签发](../images/p201523.png)

    This operation filters the certificates that are issued by CAs.

3.  Find the certificate that you want to download and click **Download** in the Actions column.

4.  In the **Download Certificate** dialog box, find the certificate for **Nginx** and click **Download** in the Actions column.

    This operation downloads the certificate package to your on-premises machine and stores the package in the default download folder of your browser.

5.  Open the folder and decompress the certificate package.

    The following two files are extracted from the package.

    ![Certificate files](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66002/156446766033690_en-US.png)

    -   CA certificate file in the PEM format

        **Note:** In this example, the certificate name `cert-file-name` is used. In actual use, you must replace it with the name of your certificate.

        The CA certificate file is encoded in Base64. You can convert the file from Privacy Enhanced Mail \(PEM\) to the required format. For more information about certificate formats, see [What formats are used for mainstream digital certificates?](/intl.en-US/Product Introduction/SSL certificate concepts/What formats are used for mainstream digital certificates?.md)

    -   Key file in the KEY format

        **Note:** If you have selected **Manual** for **CSR Generation** when you apply for the certificate, the certificate package does not contain a key file. In this case, you must manually create a key file.

        ![CSR Generation](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2536929061/p199706.png)

6.  Install the certificate on the NGINX server.

    The installation methods for NGINX servers and NGINX virtual hosts are different.

    -   For more information about how to install the certificate on an NGINX server, see [Step 2: \(Optional\) Install the certificate on an NGINX server](#section_ydh_4qb_1gb).
    -   For more information about how to install the certificate on an NGINX virtual host, see [Step 2: \(Optional\) Install the certificate on an NGINX virtual host](#section_wy0_022_q1s).

## Step 2: \(Optional\) Install the certificate on an NGINX server

1.  Log on to the NGINX server.

    You can use a remote logon tool, such as PuTTY and Xshell, to log on to the NGINX server.

2.  Run the following commands to go to the NGINX installation directory and create a directory named cert to store the certificate files. The default NGINX installation directory is /usr/local/nginx/conf.

    ```
    cd /usr/local/nginx/conf  # Go to the default NGINX installation directory. You can replace the default installation directory with the actual one.
    mkdir cert  # Create the cert directory.
    ```

3.  Invoke the file upload feature of the PuTTY or Xshell tool to upload the two certificate files to the cert directory on the NGINX server. In this example, upload the files to the /usr/local/nginx/conf/cert directory.

    **Note:** If you have selected **Manual** for **CSR Generation** when you apply for the certificate, upload the key file that you manually create to the /usr/local/nginx/conf/cert directory.

4.  Open the configuration file nginx.conf of the NGINX server to modify certificate-related information.

    1.  Run the following command to open the configuration file:

        By default, the nginx.conf file is stored in the /usr/local/nginx/conf directory. If you have moved the nginx.conf file to a new directory, replace `/usr/local/nginx/conf/nginx.conf` with the new directory.

        ```
        vim /usr/local/nginx/conf/nginx.conf
        ```

    2.  Press the I key to enter the edit mode.

    3.  Find the HTTP settings that are enclosed in `http{}` in the configuration file. Then, add the following server configurations or modify the existing server configurations based on the comments:

        The following code is only for reference. You must replace the variables with actual values.

        -   `yourdomain.com`: Replace it with the domain name that is bound to your certificate.

            If you use a single-domain certificate, enter the single domain name, such as `www.aliyun.com`. If you use a wildcard certificate, enter the wildcard domain name, such as `*.aliyun.com`.

        -   `cert-file-name.pem`: Replace it with the name of the CA certificate file that you upload in Step 3.
        -   `cert-file-name.key`: Replace it with the name of the key file that you upload in Step 3.
        ```
        # The following configuration items that start with ssl are certificate-related settings.
        server {
            listen 443 ssl;
            # Set the default HTTPS port to 443.
            # If you do not set the default HTTPS port, NGINX may fail to start.
            # If your NGINX version is 1.15.0 or later, use listen 443 ssl, instead of listen 443 and ssl on.
            server_name yourdomain.com; # Replace yourdomain.com with the domain name that is bound to your certificate.
            root html;
            index index.html index.htm;
            ssl_certificate cert/cert-file-name.pem;  # Replace cert-file-name.pem with the name of the CA certificate file that you upload.
            ssl_certificate_key cert/cert-file-name.key; # Replace cert-file-name.key with the name of the key file that you upload.
            ssl_session_timeout 5m;
            ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:! NULL:! aNULL:! MD5:! ADH:! RC4;
            # Specify the cipher suite to use.
            ssl_protocols TLSv1 TLSv1.1 TLSv1.2; # Specify the supported TLS versions.
            ssl_prefer_server_ciphers on;
            location / {
                root html;  # Specify the directory of your website.
                index index.html index.htm;
            }
        }
        ```

    4.  Redirect HTTP requests to HTTPS.

        To redirect all HTTP requests to HTTPS, you can append the `rewrite` configuration item to the domain name of the HTTP website.

        The following code is only for reference. You must replace `yourdomain.com` with the domain name that is bound to your certificate.

        ```
        server {
            listen 80;
            server_name yourdomain.com; # Replace yourdomain.com with the domain name that is bound to your certificate.
            rewrite ^(.*)$ https://$host$1; # Redirect all HTTP requests to HTTPS.
            location / {
                index index.html index.htm;
            }
        }
        ```

        **Warning:** If your website is hosted on an Alibaba Cloud Elastic Compute Service \(ECS\) instance, log on to the [ECS console](https://ecs.console.aliyun.com)[ECS console](https://partners-intl.console.aliyun.com/#/ecs) and go to the **Security Groups** page. Then, configure security group rules to allow inbound traffic to ports 80 and 443. Otherwise, your website may be inaccessible. For more information about how to configure security group rules, see [Add security group rules](/intl.en-US/Security/Security groups/Add security group rules.md).

    5.  After you modify the configuration file, press the Esc key. Then, enter :wq! and press the Enter key to save the configuration file and exit the edit mode.

5.  Run the following commands to restart the NGINX service:

    ```
    cd /usr/local/nginx/sbin  # Go to the directory that stores the NGINX executable file on the NGINX server.
    ./nginx -s reload  # Reload the configuration file.
    ```

    If an error occurs during the restart of the NGINX service, you can fix the error by using one of the following methods:

    -   If you receive the error message `the "ssl" parameter requires ngx_http_ssl_module`, recompile the NGINX program and add the `--with-http_ssl_module` configuration item when you install NGINX.
    -   If you receive the error message `"/cert/3970497_pic.certificatestests.com.pem":BIO_new_file() failed (SSL: error:02001002:system library:fopen:No such file or directory:fopen('/cert/3970497_pic.certificatestests.com.pem','r') error:2006D080:BIO routines:BIO_new_file:no such file)`, remove the forward slash \(`/`\) that precedes the relative path of the CA certificate file. For example, remove the forward slash \(`/`\) that precedes the relative path `/cert/cert-file-name.pem`. The required relative path is `cert/cert-file-name.pem`.
6.  Verify that the certificate is installed.

    For more information, see [Step 3: Verify the installation](#section_liy_o8x_gug).


## Step 2: \(Optional\) Install the certificate on an NGINX virtual host

1.  Log on to the NGINX virtual host.

2.  Create a directory named cert in the web directory. Then, copy the extracted CA certificate file and key file to the cert directory.

3.  Open the configuration file of the NGINX virtual host. Then, append the following code to the configuration file based on the comments:

    **Note:** The configuration file of virtual hosts varies based on server systems. For example, the default configuration file of an NGINX virtual host is \*.conf, and the default configuration file of an Apache virtual host is vhosts.conf. For more information about the directory of the configuration file of a virtual host, see the introduction about how to start the virtual host in the server usage notes.

    ```
    server {
        listen 80;
        server_name localhost;
        location / {
            index index.html index.htm;
        }
    }
    server {
        listen 443 ssl;
        server_name localhost;
        root html;
        index index.html index.htm;
        ssl_certificate cert/cert-file-name.pem;   # Replace cert-file-name.pem with the name of the CA certificate file that you upload.
        ssl_certificate_key cert/cert-file-name.key;   # Replace cert-file-name.key with the name of the key file that you upload.
        ssl_session_timeout 5m;
        ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:! NULL:! aNULL:! MD5:! ADH:! RC4;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_prefer_server_ciphers on;
        location / {
            index index.html index.htm;
        }
    }
    ```

4.  Save the vhost.conf file or the \*.conf file and close the file.

5.  Redirect HTTP requests to HTTPS.

    Open the .htaccess file in the web directory. If the file does not exist, create one. Add the following rewrite configuration items to redirect all HTTP requests to HTTPS:

    ```
    RewriteEngine On
    RewriteCond %{HTTP:From-Https} ! ^on$ [NC]
    RewriteCond %{HTTP_HOST} ^(www.)? yourdomain.com$ [NC]   # Replace yourdomain.com with the domain name that is bound to your certificate.
    RewriteRule ^(.*)$ https://www.yourdomain.com/$1 [R=301,L]   # Replace yourdomain.com with the domain name that is bound to your certificate.
    ```

6.  Restart the NGINX virtual host.

    **Note:** After the certificate is installed, you must configure pseudo static rules on the NGINX virtual host. This way, the entire website supports HTTPS. Otherwise, only the homepage of your website supports HTTPS, and other subdirectories do not.

7.  Verify that the certificate is installed.

    For more information, see [Step 3: Verify the installation](#section_liy_o8x_gug).


## Step 3: Verify the installation

After you complete certificate installation, you can verify it by accessing the domain name that is bound to the certificate.

```
https://yourdomain.com   # Replaces yourdomain.com with the domain name that is bound to your certificate.
```

If a lock icon appears in the address bar, the certificate is installed.

不同类型证书安装成功后的效果不同，具体如下：

-   DV SSL、OV SSL数字证书部署在服务器上后，您的浏览器访问网站时，将会展示以下效果。

    ![DV/OV证书安装效果图](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8346805061/p108043.png)

-   EV SSL数字证书部署在服务器上后，您的浏览器访问网站时，将会展示以下效果。

    ![EV证书安装效果图](../images/p108044.png)


If you encounter the following issues, troubleshoot them based on the following table.

|Issue|Possible cause|Solution|
|-----|--------------|--------|
|Your website cannot be accessed by using HTTPS.|Port 443 of the NGINX server on which you install the certificate is not enabled, or traffic to this port is blocked.|-   If your website is hosted on an Alibaba Cloud ECS instance, log on to the [ECS console](https://ecs.console.aliyun.com)[ECS console](https://partners-intl.console.aliyun.com/#/ecs) and go to the **Security Groups** page. Then, configure security group rules to allow inbound traffic to port 443.

For more information about how to configure security group rules, see [Add security group rules](/intl.en-US/Security/Security groups/Add security group rules.md).

-   If your website is not hosted on an Alibaba Cloud ECS instance, see the server instructions to allow inbound traffic to port 443. |
|The "Your connection to this site is not fully secure" message is reported.|The code of your website uses HTTP.|Change the protocol from HTTP to HTTPS in the code of your website.**Note:** The implementation logic varies based on the website code. Change the protocol based on your actual situation. If you need more support, submit a [工单](https://selfservice.console.aliyun.com/ticket/category/cas)[ticket](https://ticket-intl.console.aliyun.com/#/ticket/add/?productId=80)ticket. |
|收到网站提示“该网站未根据工信部相关法律进行备案”。|-   您的网站未完成备案，未在接入商处完成备案接入。
-   您的网站内容与备案信息不符、备案信息不准确、网站存在不适宜传播的内容等。

|-   如果您使用的是阿里ICP云备案系统，请前往[阿里云备案系统](https://beian.aliyun.com/order/index)进行网站备案。
-   如果您使用的不是阿里云ICP备案系统，请前往备案服务商的系统进行网站备案。 |

## References

-   [Install SSL certificates in Tomcat servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md)
-   [Install SSL certificates on Apache servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates on Apache servers.md)
-   [Deploy SSL certificate on Ubuntu Apache2](/intl.en-US/Install Certificates/Install certificates to servers/Deploy SSL certificate on Ubuntu Apache2.md)
-   [How do I deploy the issued certificate in Apache server]()
-   [Install SSL certificates in IIS servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates in IIS servers.md)
-   [Deploy SSL certificates on CentOS-based Tomcat 8.5 or 9.0](/intl.en-US/Install Certificates/Install certificates to servers/Deploy SSL certificates on CentOS-based Tomcat 8.5 or 9.0.md)
-   [An SSL certificate is configured by the jetty server](/intl.en-US/Install Certificates/Install certificates to servers/An SSL certificate is configured by the jetty server.md)

