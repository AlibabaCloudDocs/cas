# Install SSL certificates on JBoss servers

Alibaba Cloud SSL Certificates Service allows you to download an SSL certificate and install it on a JBoss server so that HTTPS can be enabled on the JBoss server. This topic describes how to install an SSL certificate.

1.  Check the version of your JBoss server. We recommend that you deploy the SSL certificate on JBoss 7.1.1 or later.
2.  Modify service configurations. Go to the standalone/configuration directory in the JBoss home directory and modify the standalone.xml file.

    ```
    <interfaces>
            <interface name="management">
                <inet-address value="${jboss.bind.address.management:127.0.0.1}"></inet>
            </interface>
             <!-- Enable remote access -->
            <interface name="public">
                <inet-address value="${jboss.bind.address:0.0.0.0}"></inet>
            </interface>
            <interface name="unsecure">
                <inet-address value="${jboss.bind.address.unsecure:127.0.0.1}"></inet>
            </interface>
        </interfaces>
        <socket-binding-group name="standard-sockets" default-interface="public" port-offset="${jboss.socket.binding.port-offset:0}">
            <socket-binding name="management-native" interface="management" port="${jboss.management.native.port:9999}"></socket>
            <socket-binding name="management-http" interface="management" port="${jboss.management.http.port:9990}"></socket>
            <socket-binding name="management-https" interface="management" port="${jboss.management.https.port:9443}"></socket>
            <socket-binding name="ajp" port="8009"></socket>
             <!-- Modify the HTTP port -->
            <socket-binding name="http" port="80"></socket>
              <!-- Modify the HTTPS port -->
            <socket-binding name="https" port="443"></socket>
            <socket-binding name="osgi-http" interface="management" port="8090"></socket>
            <socket-binding name="remoting" port="4447"></socket>
            <socket-binding name="txn-recovery-environment" port="4712"></socket>
            <socket-binding name="txn-status-manager" port="4713"></socket>
            <outbound-socket-binding name="mail-smtp">
                <remote-destination host="localhost" port="25"></remote>
            </outbound-socket-binding>
        </socket-binding-group>
    ```

3.  Go to the bin directory of the JBoss installation directory and run the `standalone.sh` script to ensure normal application access.
4.  Obtain the SSL certificate and convert it to the JKS format.

    Download an SSL certificate in Tomcat format from Alibaba Cloud. If you manually generate a CSR file, generate a PFX certificate key pair file. The following files are extracted:

    -   214362464370691.key
    -   214362464370691.pem
    -   214362464370691.pfx
    -   pfx-password.txt
    For a manually generated CSR file, convert the PFX certificate key pair file to the JKS format. In Windows systems, run the command in the %JAVA\_HOME%/jdk/bin directory. The following code shows an example on how to convert the format:

    ```
    openssl pkcs12 -export -out 214362464370691.pfx -inkey 214362464370691.key -in 214362464370691.pem
    ```

    Press Enter, enter the password of the JKS certificate twice, and then enter the password of the PFX certificate once. The passwords that you entered must be recorded in the pfx-password.txt file.

5.  Deploy the certificate.
    1.  Go to the standalone/configuration directory in the JBoss home directory, create a cer file, and then place the JKS certificate into the standalone/configuration folder.

        ```
        # cd /opt/jboss711/standalone/configuration
        #mkdir cert
        # pwd
        /opt/jboss711/standalone/configuration/cert
        #cp -rf /opt/keys/jboss.jks .
        ```

    2.  Modify the standalone.xml file and add certificate-related configurations.

        ```
        <subsystem xmlns="urn:jboss:domain:web:1.1" default-virtual-server="default-host" native="false">
                 <connector name="http" protocol="HTTP/1.1" scheme="http" socket-binding="http"/>
                <connector name="https" protocol="HTTP/1.1" scheme="https" socket-binding="https" secure="true">
                        <ssl name="https" password="214362464370691" certificate-key-file="../standalone/configuration/cert/jboss.jks" cipher-suite="TLS_RSA_WITH_AES_256_CBC_SHA,TLS_DHE_RSA_WITH_AES_256_CBC_SHA,TLS_DHE_DSS_WITH_AES_128_CBC_SHA,SSL_RSA_WITH_3DES_EDE_CBC_SHA,SSL_DHE_RSA_WITH_3DES_EDE_CBC_SHA,SSL_DHE_DSS_WITH_3DES_EDE_CBC_SHA" protocol="TLSv1,TLSv1.1,TLSv1.2"/>
                    </connector>
                    <virtual-server name="default-host" enable-welcome-root="true">
                        <alias name="localhost"/>
                        <alias name="example.com"/>
                    </virtual-server>
                </subsystem>
        ```

    3.  Restart the JBoss server. Go to the bin directory in the JBoss directory and run the standalone.sh script.

        ```
        #pwd
        /opt/jboss711/bin
        #sh standalone.sh &
        ```

    4.  Verify whether the SSL certificate is deployed.

        ![Verify the results](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3494088161/p4311.png)


