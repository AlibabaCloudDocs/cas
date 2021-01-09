# An SSL certificate is configured by the jetty server

1.  The jetty server version is confirmed. It is recommended that you use jetty 9.2.22 and later.
2.  Download the Tomcat certificate from Ali cloud. A non-system generated CSR requires the pfx certificate key pair file to be generated, and the conversion command is as follows.

    ```
    openssl pkcs12 -export -out 214362464370691.pfx -inkey 214362464370691.key -in 214362464370691.pem
    ```

3.  The certificate key pair file for converting pfx is in jks format, and the conversion command is as follows:

    **Note:** Note that the windows Windows environment is executed in the % java'home %/JDK/bin directory.

    ```
    Keytool-importkeystore-srckeystore key pair file. pfx-DESTIN keystore Certificate Name. jks-srcstoretype glasjks
    ```

    Enter the jks format password set twice after entering, and then enter the pfx certificate password once. You must enter the password logged in the pfx-password.txt file. The jks password is the same as the pfx certificate password, or it may cause the jetty server to fail to start.

    ![0](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/13611/15644655894312_en-US.png)

4.  Configure SSL for jetty.
    1.  Make sure that jetty's HTTP page is properly accessed.

        ![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/13611/15644655894313_en-US.png)

    2.  Copy the certificate. Enter etc under the jetty server directory, and create a new directory that holds the jks format certificate, and copy the jks format certificate to the current directory.

        ```
        # pwd
        /opt/jetty9222/etc
        # mkdir cert
        # cd cert/
        # cp .. /.. /../keys/jetty.jks .
        # ls
        jetty.jks
        ```

        ![2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/13611/15644655894314_en-US.png)

    3.  Edit the jetty-ssl.xml under etc in the jetty server directory, and set the certificate related parameters \(the password settings are the passwords recorded by pfx-password.txt\).

        ![3](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/13611/15644655904315_en-US.png)

        ```
        <? xml version="1.0"? >
        <! DOCTYPE Configure PUBLIC "-//Jetty//Configure//EN" "http://www.eclipse.org/jetty/configure_9_0.dtd">
        <! -- ============================================================= -->
        <! -- Configure a TLS (SSL) Context Factory -->
        <! -- This configuration must be used in conjunction with jetty.xml -->
        <! -- and either jetty-https.xml or jetty-spdy.xml (but not both) -->
        <! -- ============================================================= -->
        <Configure id="sslContextFactory" class="org.eclipse.jetty.util.ssl.SslContextFactory">
          <Set name="KeyStorePath"><Property name="jetty.base" default="." />/<Property name="jetty.keystore" default="etc/cert/jetty.jks"/></Set>
          <Set name="KeyStorePassword"><Property name="jetty.keystore.password" default="214362464370691"/></Set>
        <? xml version="1.0"? >
        <! DOCTYPE Configure PUBLIC "-//Jetty//Configure//EN" "http://www.eclipse.org/jetty/configure_9_0.dtd">
        <! -- ============================================================= -->
        <! -- Configure a TLS (SSL) Context Factory -->
        <! -- This configuration must be used in conjunction with jetty.xml -->
        <! -- and either jetty-https.xml or jetty-spdy.xml (but not both) -->
        <! -- ============================================================= -->
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
          <! -- =========================================================== -->
          <! -- Create a TLS specific HttpConfiguration based on the -->
          <! -- common HttpConfiguration defined in jetty.xml -->
          <! -- Add a SecureRequestCustomizer to extract certificate and -->
          <! -- session information -->
          <! -- =========================================================== -->
          <New id="sslHttpConfig" class="org.eclipse.jetty.server.HttpConfiguration">
            <Arg><Ref refid="httpConfig"/></Arg>
            <Call name="addCustomizer">
              <Arg><New class="org.eclipse.jetty.server.SecureRequestCustomizer"/></Arg>
            </Call>
          </New>
        </Configure>
        ```

    4.  Edit the jetty-https.xml under etc in the jetty server directory and configure the port used by HTTPS to be 443.

        ![4](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/13611/15644655904316_en-US.png)

        ```
        <? xml version="1.0"? >
        <! DOCTYPE Configure PUBLIC "-//Jetty//Configure//EN" "http://www.eclipse.org/jetty/configure_9_0.dtd">
        <! -- ============================================================= -->
        <! -- Configure a HTTPS connector.                                  -->
        <! -- This configuration must be used in conjunction with jetty.xml -->
        <! -- and jetty-ssl.xml.                                            -->
        <! -- ============================================================= -->
        <Configure id="Server" class="org.eclipse.jetty.server.Server">
          <! -- =========================================================== -->
          <! -- Add a HTTPS Connector.                                      -->
          <! -- Configure an o.e.j.server.ServerConnector with connection -->
          <! -- factories for TLS (aka SSL) and HTTP to provide HTTPS.      -->
          <! -- All accepted TLS connections are wired to a HTTP connection. -->
          <! --                                                             -->
          <! -- Consult the javadoc of o.e.j.server.ServerConnector, -->
          <! -- o.e.j.server.SslConnectionFactory and -->
          <! -- o.e.j.server.HttpConnectionFactory for all configuration -->
          <! -- that may be set here.                                       -->
          <! -- =========================================================== -->
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

    5.  Edit the start.ini file in the jetty server directory, change the port number as required, and set the startup to load jetty-https.xml and jetty-ssl.xml.

        ```
        jetty.port=80
        jetty.dump.stop=
        etc/jetty-ssl.xml
        etc/jetty-https.xml
        ```

    6.  Restart the jetty server and verify that the HTTPS access is normal.

        ![5](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/13611/15644655904317_en-US.png)


References:

-   [Install SSL certificates in Tomcat servers](/intl.en-US/Install Certificates/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md)
-   [Install SSL certificates on Apache servers](/intl.en-US/Install Certificates/Install SSL certificates on Apache servers.md)
-   [Deploy SSL certificate on Ubuntu Apache2](/intl.en-US/Best Practices/Deploy SSL certificate on Ubuntu Apache2.md)
-   [How do I deploy the issued certificate in Apache server]()
-   [Install an SSL certificate on an NGINX or Tengine server](/intl.en-US/Install Certificates/Install an SSL certificate on an NGINX or Tengine server.md)
-   [Install SSL certificates in IIS servers](/intl.en-US/Install Certificates/Install SSL certificates in IIS servers.md)
-   [Deploy SSL certificates on CentOS-based Tomcat 8.5 or 9.0](/intl.en-US/Best Practices/Deploy SSL certificates on CentOS-based Tomcat 8.5 or 9.0.md)

