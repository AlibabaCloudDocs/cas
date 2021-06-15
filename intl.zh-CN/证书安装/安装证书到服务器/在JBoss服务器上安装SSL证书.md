# 在JBoss服务器上安装SSL证书

阿里云SSL证书服务支持下载证书安装到JBoss服务器，从而使JBoss服务器支持HTTPS安全访问。本文介绍了证书安装的具体操作。

1.  确认JBoss版本，建议您将SSL证书部署在JBoss 7.1.1及以上版本。
2.  修改服务端口。进入JBoss主目录中的standalone/configuration，修改standalone.xml文件。

    ```
    <interfaces>
            <interface name="management">
                <inet-address value="${jboss.bind.address.management:127.0.0.1}"></inet>
            </interface>
             <!--开启远程访问-->
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
             <!--修改http端口-->
            <socket-binding name="http" port="80"></socket>
              <!--修改https端口-->
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

3.  进入JBoss安装目录的bin目录中，执行`standalone.sh`，确保应用正常访问。
4.  获取证书，并转换成jks格式。

    从阿里云下载tomcat格式的证书，非系统生成的CSR需要生成pfx证书密匙对文件，解压后文件包括：

    -   214362464370691.key
    -   214362464370691.pem
    -   214362464370691.pfx
    -   pfx-password.txt
    非系统生成的CSR，转换pfx的证书密匙对文件为jks格式（windows环境注意在%JAVA\_HOME%/jdk/bin目录中执行）。转换示例如下：

    ```
    openssl pkcs12 -export -out 214362464370691.pfx -inkey 214362464370691.key -in 214362464370691.pem
    ```

    回车后输入两次要设置的jks格式证书密码，然后输入一次pfx证书密码。三次密码必须输入pfx-password.txt记录的密码。

5.  部署证书。
    1.  进入JBoss主目录中的standalone/configuration，新建cer文件，将jks格式证书放入该文件夹。

        ```
        #​cd /opt/jboss711/standalone/configuration
        #mkdir cert
        # pwd
        /opt/jboss711/standalone/configuration/cert
        #cp -rf /opt/keys/jboss.jks .
        ```

    2.  修改standalone.xml文件，添加证书相关配置。

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

    3.  重启JBoss服务器。进入JBoss目录中的bin目录，执行standalone.sh脚本。

        ```
        #pwd
        /opt/jboss711/bin
        #sh standalone.sh &
        ```

    4.  验证。

        ![验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1390188161/p4311.png)


