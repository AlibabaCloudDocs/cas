# CentOS系统Tomcat 8.5或9部署SSL证书

本文档介绍了CentOS系统下Tomcat 8.5或9部署SSL证书的操作说明。

## 环境准备

操作系统：CentOS 7.6 64位

Web服务器：Tomcat 8.5或9

**说明：** Tomcat服务器需要提前安装JDK环境变量，请前往Tomcat官网查看推荐的JDK兼容配置。

## 前提条件

-   已从阿里云SSL证书服务控制台下载Tomcat服务器证书（包含PFX格式证书文件和TXT格式密码文件）。
-   您申请SSL证书时绑定的域名已完成DNS解析、实现了该域名指向您Tomcat服务器的IP地址。

    域名解析设置完成后执行ping www.yourdomain.com命令，如果返回了您所设置解析的主机IP地址，说明解析成功。

    ![解析](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5793571951/p38731.png)


## 操作步骤

1.  解压Tomcat证书。

    **说明：** 每次下载证书都会产生新的密码，该密码仅匹配本次下载的证书。如果需要更新证书文件，同时也要更新匹配的密码。

2.  将下载的证书和密码文件拷贝到Tomcat的**conf**目录下。

    **说明：** 如果需要安装JKS格式证书，可使用以下命令将PFX格式证书转化成JKS格式。

    ```
    keytool -importkeystore -srckeystore domain name.pfx -destkeystore domain name.jks -srcstoretype PKCS12 -deststoretype JKS
    ```

3.  打开Tomcat/conf/server.xml，在server.xml文件中找到以下参数并进行修改。

    ```
    <Connector port="8080" protocol="HTTP/1.1"
                   connectionTimeout="20000"
                   redirectPort="8443" />
    
     #找到以上参数，去掉<!- - 和 - ->这对注释符并修改为如下参数，对HTTPS默认端口进行配置：
     <Connector port="80" protocol="HTTP/1.1"   #将Connector port修改为80。
                   connectionTimeout="20000"
                   redirectPort="443" />    #将redirectPort修改为SSL默认端口443，让HTTPS请求转发到443端口。
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
    
        #找到以上参数，去掉<!- - 和 - ->这对注释符并修改为如下参数：
        <Connector port="443"   #将Tomcat中默认的HTTPS端口Connector port 8443修改为443。8443端口不可通过域名直接访问、需要在域名后加上端口号；443端口是HTTPS的默认端口，可通过域名直接访问，无需在域名后加端口号。
              protocol="org.apache.coyote.http11.Http11NioProtocol"   #server.xml文件中Connector port有两种运行模式（NIO和APR），请选择NIO模式（也就是protocol="org.apache.coyote.http11.Http11NioProtocol"）这一段进行配置。
              maxThreads="150"
              SSLEnabled="true">
            <SSLHostConfig>
                <Certificate       certificateKeystoreFile="/usr/local/tomcat/cert/证书域名.pfx"   #此处certificateKeystoreFile代表证书文件的路径，请用您证书的路径+文件名替换证书域名.pfx，例如：certificateKeystoreFile="/usr/local/tomcat/cert/abc.com.pfx"
                 certificateKeystorePassword="证书密码"   #此处certificateKeystorePassword为SSL证书的密码，请用您证书密码文件pfx-password.txt中的密码替换，例如：certificateKeystorePassword="bMNML1Df"
                 certificateKeystoreType="PKCS12" />   #证书类型为PFX格式时，certificateKeystoreType修改为PKCS12。
            </SSLHostConfig>
        </Connector>
    					
    ```

    ```
    <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />
    
    #找到以上参数，去掉<!- - 和 - ->这对注释符并修改为如下参数：
    <Connector port="8009" protocol="AJP/1.3" redirectPort="443" />  #将redirectPort修改为443，让HTTPS请求转发到443端口。
    ```

4.  保存server.xml文件配置。
5.  （可选步骤）在web.xml文件最底部添加以下内容，实现HTTP自动跳转为HTTPS。

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

6.  重启Tomcat服务。
    1.  在Tomcat下的bin目录中执行./shutdown.sh关闭Tomcat服务。

        ![关闭Tomcat服务](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5793571951/p38751.png)

    2.  在Tomcat下的bin目录中执行./startup.sh开启Tomcat服务。

        ![开启Tomcat服务](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6793571951/p38752.png)


## 后续操作

Tomcat服务重启成功后，您可在浏览器中输入您SSL证书绑定的域名https://www.YourDomainName.com验证证书安装结果。浏览器地址栏显示绿色的小锁标识说明证书安装成功。

安装证书相关文档：

-   [在Tomcat服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/Tomcat服务器安装SSL证书/安装PFX格式证书.md)
-   [在Apache服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在Apache服务器上安装SSL证书.md)
-   [Ubuntu系统Apache 2部署SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/Ubuntu系统Apache 2部署SSL证书.md)
-   [我获取到的数字证书如何配置在自己的Apache中？]()
-   [在Nginx（或Tengine）服务器上安装证书](/intl.zh-CN/证书安装/安装证书到服务器/在Nginx（或Tengine）服务器上安装证书.md)
-   [在IIS服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在IIS服务器上安装SSL证书.md)
-   [在Jetty服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在Jetty服务器上安装SSL证书.md)

