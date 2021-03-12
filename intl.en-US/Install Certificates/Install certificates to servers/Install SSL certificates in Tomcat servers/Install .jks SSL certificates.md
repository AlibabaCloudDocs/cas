# Install .jks SSL certificates

This topic describes how to install the downloaded SSL certificate in your Tomcat server. Tomcat supports both .pfx and .jks certificates. You can install a .pfx or .jks certificate based on your Tomcat version.

## Prerequisites

You selected **Automatic** for CSR Generation when applying for the certificate.

If you selected **Manual** for CSR Generation when applying for the certificate, no certificate file is generated. You have to download the .crt certificate whose Server Type is **Other**, and then run the OpenSSL command to convert the certificate to .pfx format.

In this example, the certificate name is **domain name**, and the certificate file is named **domain name.pfx**.

## Procedure

1.  Log on to the [Alibaba Cloud SSL Certificates console](https://yundunnext.console.aliyun.com/?p=casnext#/overview/cn-hangzhou).
2.  On the **SSL Certificates** page, locate the target SSL certificate and click **Download** in the lower-right corner.

    ![0](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9199797851/p33499.png)

3.  In the **Download Certificate** dialog box, locate the row that contains the certificate whose Server Type is Tomcat, and click **Download** in the **Actions** column to download the package to your local host.
4.  Decompress the package. You will obtain a certificate file \(suffixed with .pfx or of .pfx file format\) and a key file \(suffixed with .txt or of .txt file format\).

    ![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/73739/156472897644730_en-US.png)

    **Note:** Each time the certificate is downloaded, a new password is generated, which is valid only for the current certificate. To update the certificate file, you also need to update the matching key file.

5.  Run the following Java JDK command to convert the .pfx certificate file to a .jks file:

    ```
    keytool -importkeystore -srckeystore domain name.pfx -destkeystore domain name.jks -srcstoretype PKCS12 -deststoretype JKS
    ```

    **Note:** In Windows systems, you must run the preceding command in the `%JAVA_HOME%/jdk/bin` directory.

6.  Press Enter and enter the passwords in the .pfx certificate file and .jks certificate file respectively.

    **Note:** The password in the .jks certificate file must be the same as that in the .pfx certificate file. If the two passwords are different, Tomcat may fail to restart.

7.  In the **Tomcat** directory, create **cert** directory. Copy the downloaded certificate and password file to the **cert** directory.
8.  Open **Tomcat installation directory** \> **conf** \> **server.xml**. In the **server.xml** file, locate the `<Connection port="8443"`sheet and add the following parameters:

    ```
    
    #keystoreFile indicates the path of your certificate file. Replace the content after cert/ with the name of your certificate file.
    keystoreFile="cert/domain name.jks"
    keystoreType="PKCS12"
    #Replace the certificate password with the content in your key file.
    keystorePass="certificate password"
    ```

    The complete configuration is as follows \(you can modify the port attribute as needed\):

    ```
    <Connector port="8443"
        protocol="HTTP/1.1"
        SSLEnabled="true"
        scheme="https"
        secure="true"
        keystoreFile="cert/domain name.jks"
        keystoreType="PKCS12"
        keystorePass="certificate password"
        clientAuth="false"
        SSLProtocol="TLSv1+TLSv1.1+TLSv1.2"
        ciphers="TLS_RSA_WITH_AES_128_CBC_SHA,TLS_RSA_WITH_AES_256_CBC_SHA,TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA,TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256,TLS_RSA_WITH_AES_128_CBC_SHA256,TLS_RSA_WITH_AES_256_CBC_SHA256"/>
    ```

9.  Save the configuration in the server.xml file.
10. Configure web.xml file to force HTTP to jump to HTTPS.

    ```
    #Add the following after </welcome-file-list>:
    <login-config>  
        <!-- Authorization setting for SSL -->  
        <auth-method>CLIENT-CERT</auth-method>  
        <realm-name>Client Cert Users-only Area</realm-name>  
    </login-config>  
    <security-constraint>  
        <!-- Authorization setting for SSL -->  
        <web-resource-collection >  
            <web-resource-name >SSL</web-resource-name>  
            <url-pattern>/*</url-pattern>  
        </web-resource-collection>  
        <user-data-constraint>  
            <transport-guarantee>CONFIDENTIAL</transport-guarantee>  
        </user-data-constraint>  
    </security-constraint>
    ```

11. Restart Tomcat.

