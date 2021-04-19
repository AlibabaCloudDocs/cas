---
keyword: [alibaba cloud ssl certificate, apache server, support https, httpd-ssl.conf]
---

# Install SSL certificates on Apache servers

Alibaba Cloud SSL Certificates Service allows you to download an SSL certificate and install it on an Apache server so that HTTPS can be enabled on the Apache server. This topic describes how to install an SSL certificate.

-   Port 443 is enabled on your Apache server. This port is the default port for the HTTPS service
-   The mode\_ssl.so module is installed on your Apache server. This module is used to enable SSL encryption.
-   In this example, **domain name** is the certificate name, **domain name\_public.crt** is the certificate file name, **domain name\_chain.crt** is the name of the certificate chain file, and **domain name.key** is the name of the certificate key file.
-   If you do not select **Automatic** for CSR Generation when you apply for the SSL certificate, the downloaded certificate package does not include the .key file.

**Note:** A .crt certificate file is a Base64-encoded PEM file and you can modify its extension to .pem as needed. For more information about the certificate formats, see [What formats are used for mainstream digital certificates?](/intl.en-US/Product Introduction/SSL certificate concepts/What formats are used for mainstream digital certificates?.md).

## Procedure

1.  Decompress the Apache server certificate package that you downloaded to your on-premises computer.

    The following three files are extracted from the package.

    ![Certificate files](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4388678851/p33689.png)

    -   Certificate file: suffixed with .crt or of the .crt file format.
    -   Certificate chain file: suffixed with .crt or of the .crt file format.
    -   Key file: suffixed with .key or of the .key file format.
2.  Create a cert directory in the **Apache** installation directory, and copy the extracted Apache server certificate file, certificate chain file, and key file to the cert directory. To install multiple certificates, create the corresponding number of **cert** directories in the **Apache** directory to separately store the certificates.

    **Note:** If you select **Manual** for CSR Generation when you apply for the certificate, save the key file you manually created to the **cert** directory and name the key file domain name.key.

3.  Modify the httpd.conf configuration file.

    1.  In the Apache installation directory, open Apache/conf/httpd.conf, find the following parameters, and then set them based on the following annotations:

        ```
        #LoadModule ssl_module modules/mod_ssl.so  # Deletes the configuration statement annotator "#" at the beginning of the line to load the mod_ssl.so module and enable the SSL service. By default, this module is disabled on Apache servers.
        #Include conf/extra/httpd-ssl.conf # Deletes the configuration statement annotator "#" at the beginning of the line.                 
        ```

        **Note:** If you cannot find the preceding configuration statements in the httpd.conf file, check whether the mod\_ssl.so module is installed on your Apache server. You can run the `yum install -y mod_ssl` command to install the mod\_ssl.so module.

    2.  Save the httpd.conf file and exit.

4.  Modify the httpd-ssl.conf configuration file.

    1.  Open Apache/conf/extra/httpd-ssl.conf, find the following parameters, and then set them based on the following annotations:

        **Note:** The http-ssl.conf file may be stored in the conf.d/ssl.conf directory based on your service configurations.

        ```
        <VirtualHost *:443>     
            ServerName   # Changes it to the domain name www.YourDomainName1.com that you bound to your SSL certificate when you applied for the certificate.                    
            DocumentRoot  /data/www/hbappserver/public          
            SSLEngine on   
            SSLProtocol all -SSLv2 -SSLv3 # Adds supported SSL protocols and remove the ports that are not secure.
            SSLCipherSuite HIGH:!RC4:!MD5:!aNULL:!eNULL:!NULL:!DH:!EDH:!EXP:+MEDIUM   # Modifies the cipher suite.
            SSLHonorCipherOrder on
            SSLCertificateFile cert/domain name1_public.crt  # Replaces domain name1_public.crt with the name of your certificate file.
            SSLCertificateKeyFile cert/domain name1.key # Replaces domain name1.key with the name of your certificate key file.
            SSLCertificateChainFile cert/domain name1_chain.crt # Replaces domain name1_chain.crt with the name of your certificate chain file. If the name starts with a number sign (#), delete it.
        </VirtualHost>
        
        # If your certificate secures multiple domain names, copy the preceding parameters, and replace ServerName with the second domain name. 
        <VirtualHost *:443>     
            ServerName   # Changes it to the second domain name www.YourDomainName2.com that you bound to your SSL certificate when you applied for the certificate.                    
            DocumentRoot  /data/www/hbappserver/public          
            SSLEngine on   
            SSLProtocol all -SSLv2 -SSLv3 # Adds supported SSL protocols and remove the ports that are not secure.
            SSLCipherSuite HIGH:!RC4:!MD5:!aNULL:!eNULL:!NULL:!DH:!EDH:!EXP:+MEDIUM   # Modifies the cipher suite.
            SSLHonorCipherOrder on
            SSLCertificateFile cert/domain name2_public.crt # Replaces domain name2 with the second domain name that you bound to your SSL certificate when you applied for the certificate.
            SSLCertificateKeyFile cert/domain name2.key   # Replaces domain name2 with the second domain name that you bound to your SSL certificate when you applied for the certificate.
            SSLCertificateChainFile cert/domain name2_chain.crt  # Replaces domain name2 with the second domain name that you bound to your SSL certificate when you applied for the certificate. If the name starts with a number sign (#), delete it.
        </VirtualHost>
        ```

        **Note:** Check whether your browser version supports server name indication \(SNI\). If it does not support SNI, the multi-domain certificate configuration does not take effect.

    2.  Save the httpd-ssl.conf file and exit.

5.  Restart the Apache server to make the SSL configuration take effect.

    Run the following command in the bin directory of Apache:

    1.  Stop the Apache service.

        ```
        apachectl -k stop
        ```

    2.  Start the Apache service.

        ```
        apachectl -k start
        ```

6.  Modify the httpd.conf file to automatically redirect HTTP requests to HTTPS.

    Add the following redirection code to `<VirtualHost *:80> </VirtualHost>` in the httpd.conf file:

    ```
    RewriteEngine on
    RewriteCond %{SERVER_PORT} !^443$
    RewriteRule ^(.*)$ https://%{SERVER_NAME}$1 [L,R]
    ```


## What to do next

After you complete certificate installation, you can verify it by accessing the domain name that is bound to the certificate.

```
https://yourdomain.com   # Replaces yourdomain.com with the domain name that is bound to your certificate.
```

If a lock icon appears in the address bar, the certificate is installed.

If your website cannot be accessed over HTTPS after the certificate is installed, check whether the port 443 on the server where you install the certificate is enabled or blocked by other tools. If you use an Alibaba Cloud Elastic Compute Service \(ECS\) instance, log on to the ECS console and allow inbound traffic to the port 443 on the **Security Groups** page.

## References

[Install SSL certificates on Tomcat servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md)

[Deploy SSL certificate on Ubuntu Apache2](/intl.en-US/Install Certificates/Install certificates to servers/Deploy SSL certificate on Ubuntu Apache2.md)

[How do I deploy the issued certificate in Apache server]()

[Install an SSL certificate on an NGINX server or a Tengine server](/intl.en-US/Install Certificates/Install certificates to servers/Install an SSL certificate on an NGINX server or a Tengine server.md)

[Install SSL certificates in IIS servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates in IIS servers.md)

[Deploy SSL certificates on CentOS-based Tomcat 8.5 or 9.0](/intl.en-US/Install Certificates/Install certificates to servers/Deploy SSL certificates on CentOS-based Tomcat 8.5 or 9.0.md)

[Install SSL certificates on Jetty servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates on Jetty servers.md)

