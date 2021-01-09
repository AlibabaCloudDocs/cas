---
keyword: [Alibaba Cloud SSL Certificates Service, Apache server, Support HTTPS, httpd-ssl.conf]
---

# Install SSL certificates on Apache servers

Alibaba Cloud SSL Certificates Service allows you to download a certificate and install it on an Apache server so that the Apache server can be accessed over HTTPS. This topic describes how to install an SSL certificate.

-   Port 443, the default port for the HTTPS service, has been enabled on your Apache server.
-   The mod\_ssl.so module has been installed on your Apache server, which is used to enable SSL.
-   In this example, **domain name** is the certificate name, **domain name\_public.crt** is the certificate file name, **domain name\_chain.crt** is the certificate chain file, and **domain name.key** is the certificate key file.
-   If you do not select **Automatic for CSR Generation** when applying for the certificate, the downloaded certificate package will not include the .key file.

**Note:** A .crt certificate file is a Base64-encoded text file and you can modify its extension to .pem as needed. For more information about the certificate format, see [What formats are used for mainstream digital certificates?](/intl.en-US/Product Introduction/SSL certificate concepts/What formats are used for mainstream digital certificates.md).

## Procedure

1.  Decompress the downloaded certificate package.

    The following three files are extracted from the package:

    ![Certificate file](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4388678851/p33689.png)

    -   Certificate file: suffixed with .crt or of .crt file format.
    -   Certificate chain file: suffixed with .crt or of .crt file format.
    -   Key file: suffixed with .key or of .key file format.
2.  Create a cert directory in the **Apache** installation directory, and copy the downloaded Apache certificate file, certificate chain file, and key file to the cert directory. To install multiple certificates, create the corresponding number of **cert** directories in the **Apache** directory to store the certificates separately.

    **Note:** If you have selected **Manual** for CSR Generation when applying for the certificate, save the key file you created manually to the **cert** directory and name the key file as domain name.key.

3.  Modify the httpd.conf configuration file.

    1.  In the Apache installation directory, open Apache/conf/httpd.conf, find the following parameters, and configure them based on the following annotation:

        ```
        #LoadModule ssl_module modules/mod_ssl.so  # Delete the configuration statement annotator "#" at the beginning of the line to load the mod_ssl.so module and enable the SSL service. Apache does not enable this module by default.
        #Include conf/extra/httpd-ssl.conf # Delete the configuration statement annotator "#" at the beginning of the line.                 
        ```

        **Note:** If you cannot find the preceding configuration statements in the httpd.conf file, check whether the mod\_ssl.so module is installed on your Apache server. You can run the `yum install -y mod_ssl` command to install the mod\_ssl module.

    2.  Save the httpd.conf file and exit.

4.  Modify the httpd-ssl.conf configuration file.

    1.  Open Apache/conf/extra/httpd-ssl.conf, find the following parameters, and configure them based on the following annotation:

        **Note:** Depending on the operating system, the http-ssl.conf file may be stored in the conf.d/ssl.conf directory.

        ```
        <VirtualHost *:443>     
            ServerName   # Change it to the domain name www.YourDomainName1.com that was bound when you applied for the certificate.                    
            DocumentRoot  /data/www/hbappserver/public          
            SSLEngine on   
            SSLProtocol all -SSLv2 -SSLv3 # Add supported SSL protocols and remove the insecure ones.
            SSLCipherSuite HIGH:! RC4:! MD5:! aNULL:! eNULL:! NULL:! DH:! EDH:! EXP:+MEDIUM   # Modify the cipher suite.
            SSLHonorCipherOrder on
            SSLCertificateFile cert/domain name1_public.crt  # Replace domain name1_public.crt with the name of your certificate file.
            SSLCertificateKeyFile cert/domain name1.key # Replace domain name1.key with the name of your certificate key file.
            SSLCertificateChainFile cert/domain name1_chain.crt # Replace domain name1_chain.crt with the name of your certificate chain file. If the name starts with #, delete it.
        </VirtualHost>
        
        # If your certificate contains multiple domain names, copy the preceding parameters, and replace ServerName with the second domain name. 
        <VirtualHost *:443>     
            ServerName   # Change it to the second domain name www.YourDomainName2.com that was bound when you applied for the certificate.                    
            DocumentRoot  /data/www/hbappserver/public          
            SSLEngine on   
            SSLProtocol all -SSLv2 -SSLv3 # Add supported SSL protocols and remove the insecure ones.
            SSLCipherSuite HIGH:! RC4:! MD5:! aNULL:! eNULL:! NULL:! DH:! EDH:! EXP:+MEDIUM   # Modify the cipher suite.
            SSLHonorCipherOrder on
            SSLCertificateFile cert/domain name2_public.crt # Replace domain name2 with the second domain name that was bound when you applied for the certificate.
            SSLCertificateKeyFile cert/domain name2.key   # Replace domain name2 with the second domain name that was bound when you applied for the certificate.
            SSLCertificateChainFile cert/domain name2_chain.crt  # Replace domain name2 with the second domain name that was bound when you applied for the certificate. If the name starts with #, delete it.
        </VirtualHost>
        ```

        **Note:** Note that whether your browser version supports server name indication \(SNI\). If not, the multi-domain-name certificate configuration will not take effect.

    2.  Save the httpd-ssl.conf file and exit.

5.  Restart Apache to make the SSL configuration take effect.

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
    RewriteCond %{SERVER_PORT} ! ^443$
    RewriteRule ^(.*)$ https://%{SERVER_NAME}$1 [L,R]
    ```


## What to do next

After you complete the preceding operations, you can verify that the certificate is installed by accessing the domain name that is bound to the certificate.

```
https://domain name   # Replace domain name with the domain name that is bound to your certificate.
```

If the lock icon appears in the address bar, the certificate is installed.

-   When the DV SSL digital certificate is deployed on the server, you can view the following in the URL field:

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6574858951/p4190.png)

-   When the OV SSL digital certificate is deployed on the server, you can view the following in the URL field:

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6574858951/p4191.png)

-   When the EV SSL digital certificate is deployed on the server, you can view the following in the URL field:

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6574858951/p4192.png)


If your website cannot be accessed over HTTPS when you perform the preceding verification, check whether port 443 on the server where you installed the certificate is enabled or blocked by other tools.

## References

[Install SSL certificates in Tomcat servers](/intl.en-US/Install Certificates/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md)

[Deploy SSL certificate on Ubuntu Apache2](/intl.en-US/Best Practices/Deploy SSL certificate on Ubuntu Apache2.md)

[How do I deploy the issued certificate in Apache server]()

[Install an SSL certificate on an NGINX or Tengine server](/intl.en-US/Install Certificates/Install an SSL certificate on an NGINX or Tengine server.md)

[Install SSL certificates in IIS servers](/intl.en-US/Install Certificates/Install SSL certificates in IIS servers.md)

[Deploy SSL certificates on CentOS-based Tomcat 8.5 or 9.0](/intl.en-US/Best Practices/Deploy SSL certificates on CentOS-based Tomcat 8.5 or 9.0.md)

[An SSL certificate is configured by the jetty server](/intl.en-US/Install Certificates/An SSL certificate is configured by the jetty server.md)

