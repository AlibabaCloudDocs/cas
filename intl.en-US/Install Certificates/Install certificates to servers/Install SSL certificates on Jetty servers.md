# Install SSL certificates on Jetty servers

Alibaba Cloud SSL Certificates Service allows you to download an SSL certificate and install it on a Jetty server so that HTTPS can be enabled on the Jetty server. This topic describes how to install an SSL certificate.

1.  Check the version of your Jetty server. We recommend that you use Jetty 9.2.22 or later.
2.  Download a certificate in Tomcat format from Alibaba Cloud. If you manually generate a CSR file, run the following command to generate a PFX certificate key pair file:

    ```
    openssl pkcs12 -export -out 214362464370691.pfx -inkey 214362464370691.key -in 214362464370691.pem
    ```

3.  Run the following command to convert the format of the certificate key pair file from PFX to JKS:

    **Note:** In Windows systems, run the command in the %JAVA\_HOME%/jdk/bin directory.

    ```
    keytool -importkeystore -srckeystore key pair file.pfx -destkeystore certificate name.jks -srcstoretype PKCS12 -deststoretype JKS
    ```

    Press Enter, enter the password of the JKS certificate twice, and then enter the password of the PFX certificate once. The passwords that you entered must be recorded in the pfx-password.txt file. The password of the JKS certificate must be the same as that of the PFX certificate. Otherwise, the Jetty server may fail to be started.

    ![Command line execution](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/13611/15644655894312_en-US.png)

4.  Configure SSL for the Jetty server.
    1.  Make sure that you can access your Jetty server over HTTP.

        ![Confirm whether the access is normal](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/13611/15644655894313_en-US.png)

    2.  Copy the certificate. Go to the etc directory in the Jetty server directory, create a directory to store the JKS certificate, and then copy the JKS certificate to the new directory.

        ```
        # pwd
        /opt/jetty9222/etc
        # mkdir cert
        # cd cert/
        # cp ../../../keys/jetty.jks .
        # ls
        jetty.jks
        ```

        ![Command line](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/13611/15644655894314_en-US.png)

    3.  Edit the jetty-ssl.xml file in the etc directory in the Jetty server directory and set certificate-related parameters. The passwords that you set must be recorded in the pfx-password.txt file.

        ![jetty-ssl.xml file](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/13611/15644655904315_en-US.png)

        ```
        <?xml version="1.0"?>
        <!DOCTYPE Configure PUBLIC "-//Jetty//Configure//EN" "http://www.eclipse.org/jetty/configure_9_0.dtd">
        <!-- ============================================================= -->
        <!-- Configure a TLS (SSL) Context Factory                         -->
        <!-- This configuration must be used in conjunction with jetty.xml -->
        <!-- and either jetty-https.xml or jetty-spdy.xml (but not both)   -->
        <!-- ============================================================= -->
        <Configure id="sslContextFactory" class="org.eclipse.jetty.util.ssl.SslContextFactory">
          <Set name="KeyStorePath"><Property name="jetty.base" default="." />/<Property name="jetty.keystore" default="etc/cert/jetty.jks"/></Set>
          <Set name="KeyStorePassword"><Property name="jetty.keystore.password" default="214362464370691"/></Set>
        <?xml version="1.0"?>
        <!DOCTYPE Configure PUBLIC "-//Jetty//Configure//EN" "http://www.eclipse.org/jetty/configure_9_0.dtd">
        <!-- ============================================================= -->
        <!-- Configure a TLS (SSL) Context Factory                         -->
        <!-- This configuration must be used in conjunction with jetty.xml -->
        <!-- and either jetty-https.xml or jetty-spdy.xml (but not both)   -->
        <!-- ============================================================= -->
        <Configure id="sslContextFactory" class="org.eclipse.jetty.util.ssl.SslContextFactory">
          <Set name="KeyStorePath"><Property name="jetty.base" default="." />/<Property name="jetty.keystore" default="etc/cert/jetty.jks"/></Set>
          <Set name="KeyStorePassword"><Property name="jetty.keystore.password" default="214362464370691"/></Set>
          <Set name="KeyManagerPassword"><Property name="jetty.keymanager.password" default="214362464370691"/></Set>
          <Set name="TrustStorePath"><Property name="jetty.base" default="." />/<Property name="jetty.truststore" default="etc/cert/jetty.jks"/></Set>
          <Set name="TrustStorePassword"><Property name="jetty.truststore.password" default="214362464370691"/></Set>
          <Set name="EndpointIdentificationAlgorithm"></Set>
          <Set name="NeedClientAuth"><Property name="jetty.ssl.needClientAuth" default="false"/></Set>
          <Set name="WantClientAuth"><Property name="jetty.ssl.wantClientAuth" default="false"/></Set>
          <Set name="ExcludeCipherSuites">
            <Array type="String">
              <Item>SSL_RSA_WITH_DES_CBC_SHA</Item>
              <Item>SSL_DHE_RSA_WITH_DES_CBC_SHA</Item>
              <Item>SSL_DHE_DSS_WITH_DES_CBC_SHA</Item>
              <Item>SSL_RSA_EXPORT_WITH_RC4_40_MD5</Item>
              <Item>SSL_RSA_EXPORT_WITH_DES40_CBC_SHA</Item>
              <Item>SSL_DHE_RSA_EXPORT_WITH_DES40_CBC_SHA</Item>
              <Item>SSL_DHE_DSS_EXPORT_WITH_DES40_CBC_SHA</Item>
            </Array>
          </Set>
          <!-- =========================================================== -->
          <!-- Create a TLS specific HttpConfiguration based on the        -->
          <!-- common HttpConfiguration defined in jetty.xml               -->
          <!-- Add a SecureRequestCustomizer to extract certificate and    -->
          <!-- session information                                         -->
          <!-- =========================================================== -->
          <New id="sslHttpConfig" class="org.eclipse.jetty.server.HttpConfiguration">
            <Arg><Ref refid="httpConfig"/></Arg>
            <Call name="addCustomizer">
              <Arg><New class="org.eclipse.jetty.server.SecureRequestCustomizer"/></Arg>
            </Call>
          </New>
        </Configure>
        ```

    4.  Edit the jetty-https.xml file in the etc directory in the Jetty server directory and configure port 443 for the HTTPS service.

        ![jetty-https.xml file](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/13611/15644655904316_en-US.png)

        ```
        <?xml version="1.0"?>
        <!DOCTYPE Configure PUBLIC "-//Jetty//Configure//EN" "http://www.eclipse.org/jetty/configure_9_0.dtd">
        <!-- ============================================================= -->
        <!-- Configure a HTTPS connector.                                  -->
        <!-- This configuration must be used in conjunction with jetty.xml -->
        <!-- and jetty-ssl.xml.                                            -->
        <!-- ============================================================= -->
        <Configure id="Server" class="org.eclipse.jetty.server.Server">
          <!-- =========================================================== -->
          <!-- Add a HTTPS Connector.                                      -->
          <!-- Configure an o.e.j.server.ServerConnector with connection   -->
          <!-- factories for TLS (aka SSL) and HTTP to provide HTTPS.      -->
          <!-- All accepted TLS connections are wired to a HTTP connection.-->
          <!--                                                             -->
          <!-- Consult the javadoc of o.e.j.server.ServerConnector,        -->
          <!-- o.e.j.server.SslConnectionFactory and                       -->
          <!-- o.e.j.server.HttpConnectionFactory for all configuration    -->
          <!-- that may be set here.                                       -->
          <!-- =========================================================== -->
          <Call id="httpsConnector" name="addConnector">
            <Arg>
              <New class="org.eclipse.jetty.server.ServerConnector">
                <Arg name="server"><Ref refid="Server" /></Arg>
                <Arg name="acceptors" type="int"><Property name="ssl.acceptors" default="-1"/></Arg>
                <Arg name="selectors" type="int"><Property name="ssl.selectors" default="-1"/></Arg>
                <Arg name="factories">
                  <Array type="org.eclipse.jetty.server.ConnectionFactory">
                    <Item>
                      <New class="org.eclipse.jetty.server.SslConnectionFactory">
                        <Arg name="next">http/1.1</Arg>
                        <Arg name="sslContextFactory"><Ref refid="sslContextFactory"/></Arg>
                      </New>
                    </Item>
                    <Item>
                      <New class="org.eclipse.jetty.server.HttpConnectionFactory">
                        <Arg name="config"><Ref refid="sslHttpConfig"/></Arg>
                      </New>
                    </Item>
                  </Array>
                </Arg>
                <Set name="host"><Property name="jetty.host" /></Set>
                <Set name="port"><Property name="https.port" default="443" /></Set>
                <Set name="idleTimeout"><Property name="https.timeout" default="30000"/></Set>
                <Set name="soLingerTime"><Property name="https.soLingerTime" default="-1"/></Set>
                <Set name="acceptorPriorityDelta"><Property name="ssl.acceptorPriorityDelta" default="0"/></Set>
                <Set name="selectorPriorityDelta"><Property name="ssl.selectorPriorityDelta" default="0"/></Set>
                <Set name="acceptQueueSize"><Property name="https.acceptQueueSize" default="0"/></Set>
              </New>
            </Arg>
          </Call>
        </Configure>
        ```

    5.  Edit the start.ini file in the Jetty server directory, change the port number as needed, and then configure automatic loading of jetty-https.xml and jetty-ssl.xml upon server startup.

        ```
        jetty.port=80
        jetty.dump.stop=
        etc/jetty-ssl.xml
        etc/jetty-https.xml
        ```

    6.  Restart the Jetty server and check whether you can access it over HTTPS.

        ![Verify the results](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/13611/15644655904317_en-US.png)


References

-   [Install SSL certificates on Tomcat servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md)
-   [Install SSL certificates on Apache servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates on Apache servers.md)
-   [Deploy SSL certificate on Ubuntu Apache2](/intl.en-US/Install Certificates/Install certificates to servers/Deploy SSL certificate on Ubuntu Apache2.md)
-   [How do I deploy the issued certificate on my Apache server?]()
-   [Install an SSL certificate on an NGINX server or a Tengine server](/intl.en-US/Install Certificates/Install certificates to servers/Install an SSL certificate on an NGINX server or a Tengine server.md)
-   [Install SSL certificates in IIS servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates in IIS servers.md)
-   [Deploy SSL certificates on CentOS-based Tomcat 8.5 or 9.0](/intl.en-US/Install Certificates/Install certificates to servers/Deploy SSL certificates on CentOS-based Tomcat 8.5 or 9.0.md)

