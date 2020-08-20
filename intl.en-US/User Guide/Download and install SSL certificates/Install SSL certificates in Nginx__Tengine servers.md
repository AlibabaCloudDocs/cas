# Install SSL certificates in Nginx/Tengine servers {#concept_n45_21x_yfb .concept}

This topic describes how to download an SSL certificate from the Alibaba Cloud SSL Certificates console and install it in your Nginx/Tengine server.

## Prerequisites {#section_xdh_4qb_1gb .section}

You selected **Automatic** for CSR Generation when applying for the certificate.

In this example, the certificate name is **domain name**, the certificate file is named **domain name.pem** and the key file is named **domain name.key**.

## Procedure {#section_ydh_4qb_1gb .section}

1.  Log on to the Alibaba Cloud SSL Certificates console.
2.  On the **SSL Certificates** page, locate the target SSL certificate and click **Download** in the lower-right corner.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66242/156446765933499_en-US.png)

3.  In the **Download Certificate** dialog box, locate the row that contains the certificate whose Server Type is Nginx/Tengine, and click **Download** in the **Actions** column to download the package to your local host.
4.  Decompress the package.

    The following two files are extracted:

    -   Certificate file \(suffixed with .pem or of .pem file format\)
    -   Key file \(suffixed with .key or of .key file format\)
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66002/156446765933690_en-US.png)

    **Note:** The **.pem** certificate file is a Base64-encoded text file and you can modify its extension as needed.

    For more information about the certificate format, see [What are the formats of mainstream digital certificates?](https://partners-intl.aliyun.com/help/faq-detail/42214.htm)

5.  Create a **cert** directory in the Nginx installation directory, and copy the downloaded certificate file and key file to the **cert** directory.

    **Note:** If you have selected **Manual** for CSR Generation when applying for the certificate, place the private key file in the **cert** directory.

6.  Open **Nginx installation directory** \> **conf** \> **nginx.conf**. In the **nginx.conf** file, locate the following attributes:

    ``` {#codeblock_nlm_9vo_0ps}
    
    # HTTPS server
      server {
      listen 443;
      server_name localhost;
      ssl on;
      ssl_certificate cert.pem;
      ssl_certificate_key cert.key;
      ssl_session_timeout 5m;
      ssl_protocols SSLv2 SSLv3 TLSv1;
      ssl_ciphers ALL:! ADH:! EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP;
      ssl_prefer_server_ciphers on;
      location / {
    						
    ```
    Note that on Ubuntu, you may not find the above attributes in nginx.conf, instead, they are located in /etc/nginx/sites-enabled/default.
    
    Modify the nginx.conf file as follows:

    ``` {#codeblock_xt8_f4t_yvg}
    
    # The attributes that start with "ssl" are related to certificate configurations, while the others can be configured as needed.
    server {
    listen 443;
    server_name localhost;  # Replace localhost with the domain name bound to your certificate.
    ssl on;   #Set this attribute to On to enable the SSL function.
    root html;
    index index.html index.htm;
    ssl_certificate cert/domain name.pem;   #Replace domain name.pem with the name of your certificate file.
    ssl_certificate_key cert/domain name.key;   #Replace domain name.key with the name of your private key file.
    ssl_session_timeout 5m;
    ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:! NULL:! aNULL:! MD5:! ADH:! RC4;  #Use this cipher suite.
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;   #Change protocols.
    ssl_prefer_server_ciphers on;   
    location / {
    root html;   #Set the site directory.
    index index.html index.htm;   #Add an attribute.
    }
    }
    							
    ```

7.  （optional）Configurec http request to force to jump to https，and you can access via use http protocol. Modify nginx.conf file as follows:

    ``` {#codeblock_487_ck7_4vn}
    server {
        listen 80;
        server_name localhost;  #replace localhost with domain name bound by the certificate.
        return    301 https://$server_name$request_uri; 
    }
    server { 
        listen 443 ssl; 
        server_name localhost;  #replace localhost with domain name bound by the certificate.
    }
    ```

8.  Save the **nginx.conf** file and exit.
9.  Restart the Nginx server.

References:

-   [Install SSL certificates in Tomcat servers](reseller.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md#)
-   [Install SSL certificates in Apache servers](reseller.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in Apache servers.md#)
-   [Deploy SSL certificate on Ubuntu Apache2](../../../../reseller.en-US/Best Practices/Deploy SSL certificate on Ubuntu Apache2.md#)
-   [How do I deploy the issued certificate in Apache server](../../../../reseller.en-US/FAQ/FAQ/How do I deploy the issued certificate in Apache server.md#)
-   [Install SSL certificates in IIS servers](reseller.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in IIS servers.md#)
-   [Deploy SSL certificates on Tomcat 8.5 or Tomcat 9.0 running CentOS](../../../../reseller.en-US/Best Practices/Deploy SSL certificates on Tomcat 8.5 or Tomcat 9.0 running CentOS.md#)
-   [An SSL certificate is configured by the jetty server](../../../../reseller.en-US/FAQ/FAQ/An SSL certificate is configured by the jetty server.md#)

