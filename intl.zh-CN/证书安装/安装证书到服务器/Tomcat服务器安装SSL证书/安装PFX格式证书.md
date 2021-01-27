---
keyword: [阿里云SSL证书, Tomcat服务器, 支持HTTPS]
---

# 安装PFX格式证书

阿里云SSL证书服务支持下载证书安装到Tomcat服务器上。Tomcat支持PFX格式和JKS两种格式的证书，您可根据您Tomcat的版本择其中一种格式的证书安装到Tomcat上。本文介绍了PFX格式证书安装的具体步骤。

-   您的Tomcat服务器上已经开启了443端口（HTTPS服务的默认端口）。
-   已安装OpenSSL工具。
-   已下载Tomcat服务器所需要的证书文件。有关证书下载的具体操作，请参见[下载证书](/intl.zh-CN/证书安装/下载证书.md)。

    **说明：**

    -   申请证书时如果未选择**系统自动创建CSR**，证书下载压缩包中将不包含TXT文件。需要您选择**其他**类型服务器下载CRT证书，并使用openssl命令生成PFX文件。
    -   如果您自己拥有其他证书，可使用openssl命令将您自己的证书文件转化为相应格式的文件，安装到Tomcat服务器上。
-   已登录您的Tomcat服务器。

-   本文教程以Tomcat 7为例。
-   Tomcat 9强制要求证书别名设置为tomcat。您需要使用以下keytool命令将`protocol="HTTP/1.1"`转换成`protocol="org.apache.coyote.http11.Http11NioProtocol"`。

    ```
    keytool -changealias -keystore domain name.pfx -alias alias -destalias tomcat
    ```

-   本文档证书名称以**domain name**为示例。例如，证书文件名称为domain name.pfx，证书密码文件名称为pfx-password.txt。

## 操作步骤

1.  解压已下载保存到本地的Tomcat证书文件。

    解压后您将看到文件夹中有2个文件，您可为两个证书文件重命名。

    -   证书文件（domain name.pfx）：以PFX为文件类型。
    -   密码文件（pfx-password.txt）：以TXT为文件类型。
    ![证书文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1242336851/p33514.png)

    **说明：** 每次下载证书都会产生新的密码，该密码仅匹配本次下载的证书。如果需要更新证书文件，同时也要更新匹配的密码。

2.  在Tomcat安装目录下新建cert目录，将解压的证书和密码文件拷贝到cert目录下。

3.  修改配置文件server.xml（路径：Tomcat安装目录/conf/server.xml），并保存。

    1.  去掉以下内容的注释：

        ```
        <Connector  port="8443"
        protocol="HTTP/1.1"
          SSLEnabled="true"
          maxThreads="150" scheme="https" secure="true"
          clientAuth="false" sslProtocol="TLS" />
        ```

    2.  参照以下内容修改`<Connector port="443"`标签内容。

        ```
        <Connector port="443"   #port属性根据实际情况修改（https默认端口为443）。如果使用其他端口号，则您需要使用https://yourdomain:port的方式来访问您的网站。
            protocol="HTTP/1.1"
            SSLEnabled="true"
            scheme="https"
            secure="true"
            keystoreFile="Tomcat安装目录/cert/domain name.pfx" #证书名称前需加上证书的绝对路径，请使用您证书的文件名替换domain name。
            keystoreType="PKCS12"
            keystorePass="证书密码"  #请替换为密码文件pfx-password.txt中的内容。
            clientAuth="false"
            SSLProtocol="TLSv1+TLSv1.1+TLSv1.2"
            ciphers="TLS_RSA_WITH_AES_128_CBC_SHA,TLS_RSA_WITH_AES_256_CBC_SHA,TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA,TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256,TLS_RSA_WITH_AES_128_CBC_SHA256,TLS_RSA_WITH_AES_256_CBC_SHA256"/>
        ```

4.  配置web.xml文件，开启HTTP强制跳转HTTPS。

    在文件</welcome-file-list\>后添加以下内容：

    ```
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

5.  重启Tomcat。

    1.  执行以下命令关闭Tomcat服务器。

        ```
        ./shutdown.sh
        ```

    2.  执行以下命令开启Tomcat服务器。

        ```
        ./startup.sh
        ```


## 后续操作

证书安装完成后，可通过登录证书绑定域名的方式验证证书是否安装成功。

```
https://domain name.com   #domain name替换成证书绑定的域名。
```

如果网页地址栏出现绿色小锁标志，表示证书安装成功。

验证证书是否安装成功时，如果网站无法通过https正常访问，需确认您安装证书的服务器443端口是否已开启或被其他工具拦截。

## 相关文档

[在Tomcat服务器上安装JKS格式的证书](/intl.zh-CN/证书安装/安装证书到服务器/Tomcat服务器安装SSL证书/安装JKS格式证书.md)

[CentOS系统Tomcat 8.5或9部署SSL证书](/intl.zh-CN/最佳实践/CentOS系统Tomcat 8.5或9部署SSL证书.md)

[Ubuntu系统Apache 2部署SSL证书](/intl.zh-CN/最佳实践/Ubuntu系统Apache 2部署SSL证书.md)

[我获取到的数字证书如何配置在自己的Apache中？]()

[在Nginx（或Tengine）服务器上安装证书](/intl.zh-CN/证书安装/安装证书到服务器/在Nginx（或Tengine）服务器上安装证书.md)

[在IIS服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在IIS服务器上安装SSL证书.md)

[在Jetty服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在Jetty服务器上安装SSL证书.md)

