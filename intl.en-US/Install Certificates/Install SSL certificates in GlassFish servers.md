# Install SSL certificates in GlassFish servers

This topic describes how to install your SSL certificate in a GlassFish server.

## Procedure

In this example, the SSL certificate name is **cer01**, the certificate file is named **cer01.pem** and the key file is named **cer01.key**.

1.  Log on to the [Alibaba Cloud SSL Certificates console](https://yundunnext.console.aliyun.com/?p=casnext#/overview/cn-hangzhou).
2.  On the **SSL Certificates** page, locate the target SSL certificate and click **Download** in the lower-right corner.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9199797851/p33499.png)

3.  In the **Download Certificate** dialog box, locate the row that contains the SSL certificate whose Server Type is **Other**, and click **Download** in the **Actions** column to download the package to your local host.
4.  Decompress the package. You will obtain a certificate file \(suffixed with .pem or of .pem file format\) and a key file \(suffixed with .txt or of .txt file format\).

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/77568/156888038934118_en-US.png)

5.  Run the following commands to convert the certificate file and key file to .jks files:

    ```
    openssl pkcs12 -export -in cer01.pem -inkey cer01.key -out temp.p12 -passout pass:changeit -name s1as
    #Replace cer01.pem with the name of your certificate file, and replace cer01.key with the name of your key file. The password that you set when converting the certificate format must be the same as the certificate password on the GlassFish server. The default password is changeit.
    ```

    ```
    keytool -importkeystore -srckeystore temp.p12 -srcstoretype PKCS12 -srcstorepass changeit -deststoretype JKS -destkeystore ./glassfish5/glassfish/domains/domain1/config/keystore.jks -deststorepass changeit -alias s1as
    #The password that you set when converting the certificate format must be the same as the certificate password on the GlassFish server. The default password is changeit.
    ```

6.  Restart the domain.

    ```
    ./glassfish5/bin/asadmin restart-domain
    ```

7.  Check whether the domain name bound to your Alibaba Cloud SSL certificate is valid.

    ```
    wget https://127.0.0.1:8181
    ```


