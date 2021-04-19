---
keyword: [alibaba cloud ssl certificate, glassfish server, support https]
---

# Install SSL certificates on GlassFish servers

Alibaba Cloud SSL Certificates Service allows you to download an SSL certificate and install it on a GlassFish server. This topic describes how to install an SSL certificate on a GlassFish server.

In this example, **cer01** is the certificate name, **cer01.pem** is the certificate file name, and **cer01.key** is the name of the certificate key file.

## Procedure

1.  Log on to the [SSL Certificates Service console](https://yundun.console.aliyun.com/?p=cas).

2.  On the SSL Certificates Service page, find the certificate that you want to download, and click **Download** in the Actions column.

3.  Find **Other** in the Server Type column and click **Download** in the **Actions** column to download the certificate package to your on-premises computer.

4.  Decompress the certificate package that you downloaded. Two files are extracted, including a certificate file suffixed with PEM or of the PEM file format and a key file suffixed with TXT or of the TXT file format.

    ![Certificate files](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/77568/156888038934118_en-US.png)

5.  Run the following commands to convert the certificate file and the key file to JKS files:

    ```
    openssl pkcs12 -export -in cer01.pem -inkey cer01.key -out temp.p12 -passout pass:changeit -name s1as
    #Replaces cer01.pem with the name of your certificate file, and replace cer01.key with the name of your certificate key file. The password that you set when you convert the certificate format must be the same as the certificate password on the GlassFish server. The default password is changeit. 
    ```

    ```
    keytool -importkeystore -srckeystore temp.p12 -srcstoretype PKCS12 -srcstorepass changeit -deststoretype JKS -destkeystore ./glassfish5/glassfish/domains/domain1/config/keystore.jks -deststorepass changeit -alias s1as
    #The password that you set when you convert the certificate format must be the same as the certificate password on the GlassFish server. The default password is changeit. 
    ```

6.  Restart the domain.

    ```
    ./glassfish5/bin/asadmin restart-domain
    ```

7.  Check whether the domain name bound to your Alibaba Cloud SSL certificate is valid.

    ```
    wget https://10.0.0.1:8181
    ```


