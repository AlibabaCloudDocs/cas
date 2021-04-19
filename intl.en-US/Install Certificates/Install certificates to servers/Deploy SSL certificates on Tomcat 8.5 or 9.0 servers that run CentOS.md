# Deploy SSL certificates on Tomcat 8.5 or 9.0 servers that run CentOS

This topic describes how to deploy an SSL certificate on a Tomcat 8.5 or Tomcat 9.0 server that runs CentOS.

## Environments

Operating system: CentOS 7.6, 64-bit

Web server: Tomcat 8.5 or Tomcat 9.0

**Note:** JDK environment variables must be set on the Tomcat server first. You can view the recommended JDK-compatible configurations on the Tomcat official website.

## Prerequisites

-   The Tomcat server certificate is downloaded from the SSL Certificates Service console. The Tomcat server certificate includes a certificate file in PFX format and a password file in TXT format.
-   DNS resolution is configured for the domain name that you bound to your SSL certificate when you applied for this certificate, and the domain name points to the IP address of your Tomcat server.

    Run the ping www.yourdomain.com command after the domain name resolution is configured. If the IP address of your Tomcat server is returned, the resolution is successful.

    ![Resolution](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7270588851/p38731.png)


## Procedure

1.  Decompress the Tomcat server certificate package.

    **Note:** A new password file is generated each time you download the certificate. The password is valid only for the certificate you download that time. If you need to update the certificate file, you must also update the matching password file.

2.  Copy the downloaded certificate and password files to the **conf** directory of your Tomcat server.

    **Note:** To install a JKS certificate, run the following command to convert the format of the certificate from PFX to JKS:

    ```
    keytool -importkeystore -srckeystore domain name.pfx -destkeystore domain name.jks -srcstoretype PKCS12 -deststoretype JKS
    ```

3.  Open Tomcat/conf/server.xml, find the following parameters in the server.xml file, and modify these parameters.

    ```
    <Connector port="8080" protocol="HTTP/1.1"
                   connectionTimeout="20000"
                   redirectPort="8443" />
    
     #Find the preceding parameters, remove the <!- - and - -> annotation symbols, and modify the parameters based on the following annotations to configure the default HTTPS port:
     <Connector port="80" protocol="HTTP/1.1"   #Sets connector port to 80.
                   connectionTimeout="20000"
                   redirectPort="443" />    #Sets redirectPort to the default SSL port 443 to redirect HTTPS requests to this port. 
    ```

    ```
    
    
        <Connector port="8443"
              protocol="org.apache.coyote.http11.Http11NioProtocol"
              maxThreads="150"
              SSLEnabled="true">
            <SSLHostConfig>
                <Certificate       certificateKeystoreFile="cert/keystore.pfx"
                 certificateKeystorePassword="XXXXXXX"
                             certificateKeystoreType="PKCS12" />
    
        #Find the preceding parameters, remove the <!- - and - -> annotation symbols, and modify the parameters based on the following annotations:
        <Connector port="443"   # Changes the connector port from 8443 to the default Tomcat HTTPS port 443. Port 8443 cannot be directly accessed by using the domain name. Therefore, you must append a port number to the domain name. Port 443 is the default HTTPS port. You can directly access this port by using the domain name without the need to append a port number to the domain name.
              protocol="org.apache.coyote.http11.Http11NioProtocol"   #The connector port in the server.xml file has two modes: NIO and APR. In this deployment, the NIO mode is used. protocol="org.apache.coyote.http11.Http11NioProtocol" indicates the NIO mode.
              maxThreads="150"
              SSLEnabled="true">
            <SSLHostConfig>
                <Certificate       certificateKeystoreFile="/usr/local/tomcat/cert/Certificate Domain Name.pfx"   #The certificateKeystoreFile parameter indicates the path of the certificate file. Replace Certificate Domain Name.pfx with the path and name of your certificate file, such as certificateKeystoreFile="/usr/local/tomcat/cert/abc.com.pfx".
                 certificateKeystorePassword="Certificate password"   #The certificateKeystorePassword parameter indicates the password for the SSL certificate. Replace it with your certificate password in the pfx-password.txt file, such as certificateKeystorePassword="bMNML1Df".
                 certificateKeystoreType="PKCS12" />   #When the certificate type is PFX, set certificateKeystoreType to PKCS12.
            </SSLHostConfig>
        </Connector>
                        
    ```

    ```
    <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />
    
    #Find the preceding parameters, remove the <!- - and - -> annotation symbols, and modify the parameters based on the following annotations:
    <Connector port="8009" protocol="AJP/1.3" redirectPort="443" />  #Sets redirectPort to 443 to redirect HTTPS requests to this port. 
    ```

4.  Save the configurations in the server.xml file.
5.  Optional. Add the following content at the bottom of the web.xml file to automatically redirect HTTP requests to HTTPS:

    ```
    <security-constraint> 
             <web-resource-collection > 
                  <web-resource-name >SSL</web-resource-name>  
                  <url-pattern>/*</url-pattern> 
           </web-resource-collection> 
           <user-data-constraint> 
                        <transport-guarantee>CONFIDENTIAL</transport-guarantee> 
           </user-data-constraint> 
        </security-constraint>
    ```

6.  Restart the Tomcat service.
    1.  Run the ./shutdown.sh script in the bin directory of your Tomcat server to disable the Tomcat service.

        ![Disable the Tomcat service](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7270588851/p38751.png)

    2.  Run the ./startup.sh script in the bin directory of your Tomcat server to enable the Tomcat service.

        ![Enable the Tomcat service](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8270588851/p38752.png)


## What to do next

After the Tomcat service is restarted, enter https://www.YourDomainName.com in the address bar of your browser to verify whether the SSL certificate is installed. It is the domain name that you bound to your SSL certificate. If the green lock icon appears in the address bar of your browser, the SSL certificate is installed.

References

-   [Install SSL certificates on Tomcat servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md)
-   [Install SSL certificates on Apache servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates on Apache servers.md)
-   [Deploy SSL certificate on Ubuntu Apache2](/intl.en-US/Install Certificates/Install certificates to servers/Deploy SSL certificate on Ubuntu Apache2.md)
-   [How do I deploy the issued certificate in Apache server]()
-   [Install an SSL certificate on an NGINX server or a Tengine server](/intl.en-US/Install Certificates/Install certificates to servers/Install an SSL certificate on an NGINX server or a Tengine server.md)
-   [Install SSL certificates in IIS servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates in IIS servers.md)
-   [Install SSL certificates on Jetty servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates on Jetty servers.md)

