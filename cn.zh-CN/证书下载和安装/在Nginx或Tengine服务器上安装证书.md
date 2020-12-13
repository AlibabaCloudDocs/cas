---
keyword: [阿里云SSL证书, Nginx服务器, Tengine服务器, 支持HTTPS]
---

# 在Nginx或Tengine服务器上安装证书

阿里云SSL证书服务支持下载证书并安装到Nginx、Tengine服务器上。本文介绍了安装证书的具体操作。

已准备好远程登录工具，例如PuTTY或者Xshell。

-   本文以CentOS 8、Nginx 1.14.1为例进行说明。由于版本不同，您在操作过程中的命令可能会略有区别。
-   本文中证书名称以**domain name**为例，例如，证书文件名称为**domain name.pem**、证书密钥文件名称为**domain name.key**。
-   下载的Nginx证书压缩文件解压后包含：
    -   PEM证书文件。
    -   KEY证书密钥文件。申请证书时如果未选择**自动创建CRS**，则下载的证书文件压缩包中不会包含KEY文件，需要您自己手动创建证书密钥文件。

**说明：** PEM证书文件是采用Base64编码的文本文件，您可根据需要修改成其他扩展名。关于证书格式的详细内容，请参见[主流数字证书都有哪些格式](/cn.zh-CN/产品简介/常见问题/主流数字证书都有哪些格式？.md)。

## 操作步骤

1.  登录阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)。

2.  在左侧导航栏，单击**概览**。

3.  在SSL证书页面，定位到需要下载的证书实例，单击**下载**。

4.  在**证书下载**页面，定位到**Nginx**服务器，单击右侧**操作**列的**下载**，将Nginx服务器证书压缩包下载到本地。

5.  解压已下载保存到本地的Nginx证书压缩包文件。

    解压后的文件夹中有2个文件：

    -   证书文件：文件类型为PEM。
    -   密钥文件：文件类型为KEY。
    ![证书文件](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8267997951/p33690.png)

6.  登录您的Nginx服务器，在Nginx安装目录（默认为/usr/local/nginx/conf）执行以下命令，创建**cert**目录：

    ```
    cd /usr/local/nginx/conf  #进入Nginx默认安装目录。此处为Nginx默认安装目录，请您根据实际配置情况操作。
    mkdir cert  #创建cert证书目录。
    ```

7.  使用远程登录工具（例如PuTTY或者Xshell）附带的本地文件上传功能，将下载的证书文件和密钥文件上传到Nginx服务器的**cert**目录下。

    **说明：** 如果您在申请证书时选择**手动创建CSR**文件，请将您自己手动创建的证书密钥文件上传到**cert**目录下，并命名为**domain name.key**。

8.  执行以下命令，打开Nginx安装目录/conf/nginx.conf配置文件并进行编辑。

    ```
    vim /usr/local/nginx/conf/nginx.conf #打开配置文件。此处为Nginx默认配置文件目录，请您根据实际配置情况操作。
    ```

    按**i**键进入编辑模式，在配置文件中找到HTTP协议代码片段，在HTTP协议代码里面新增以下server配置示例。如果server配置已存在，按照以下注释内容修改相应的配置即可。

    ```
    #以下属性中以ssl开头的属性代表与证书配置有关，其他属性请根据自己的需要进行配置。
    server {
             listen 443 ssl; #配置HTTPS的默认访问端口号为443。此处如果未配置HTTPS的默认访问端口，可能会造成Nginx无法启动。Nginx 1.15.0以上版本请使用listen 443 ssl代替listen 443和ssl on。
             server_name www.certificatestests.com; #将www.certificatestests.com修改为您证书绑定的域名，例如：www.example.com。如果您购买的是通配符域名证书，要修改为通配符域名，例如：*.aliyun.com。
             root html;
             index index.html index.htm;
             ssl_certificate cert/domain name.pem;  #将domain name.pem替换成您证书的文件名称。
             ssl_certificate_key cert/domain name.key; #将domain name.key替换成您证书的密钥文件名称。
             ssl_session_timeout 5m;
             ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4; #使用此加密套件。
             ssl_protocols TLSv1 TLSv1.1 TLSv1.2; #使用该协议进行配置。
             ssl_prefer_server_ciphers on;
             location / {
             root html;  #站点目录。
             index index.html index.htm;
                        }
          }
    ```

    配置文件修改完毕之后，按**Esc**键后输入:wq！，然后按**Enter**键保存修改的配置文件并退出编辑模式。

9.  执行以下命令，进入Nginx服务器的可执行目录**sbin**并重启Nginx服务器。

    ```
    cd /usr/local/nginx/sbin  #进入Nginx服务器的可执行目录**sbin**。
    ./nginx -s reload  #重启Nginx服务器。
    ```

    **说明：**

    -   如果重启Nginx服务器出现`the "ssl" parameter requires ngx_http_ssl_module`报错，您需要重新编译Nginx并在编译安装的时候加上`--with-http_ssl_module`配置。
    -   如果重启Nginx服务器出现`"/cert/3970497_pic.certificatestests.com.pem":BIO_new_file() failed (SSL: error:02001002:system library:fopen:No such file or directory:fopen('/cert/3970497_pic.certificatestests.com.pem','r') error:2006D080:BIO routines:BIO_new_file:no such file)`报错，您需要去掉证书相对路径最前面的`/`。例如，您需要去掉`/cert/3970497_pic.certificatestests.com.pem`最前面的`/`，使用正确的相对路径`cert/3970497_pic.certificatestests.com.pem`。
10. 设置HTTP请求自动跳转HTTPS。

    在需要跳转的HTTP站点下添加以下rewrite语句，实现HTTP访问自动跳转到HTTPS页面。

    ```
    server {
     listen 80;
     server_name www.certificatestests.com; #将www.certificatestests.com修改为您证书绑定的域名，例如：www.example.com。
    rewrite ^(.*)$ https://$host$1 permanent;   #将所有HTTP请求通过rewrite重定向到HTTPS。
     location / {
    index index.html index.htm;
    }
    }
    ```


## 虚拟主机配置SSL证书

1.  登录您的虚拟机，在Web目录下创建**cert**目录，并将下载的证书文件和密钥文件拷贝到**cert**目录中。

2.  打开虚拟主机配置文件vhost.conf或\*.conf，复制以下内容粘贴到文件末尾、将端口改为443（HTTPS默认端口）并增加证书相关配置。

    ```
    server {
     listen 80;
     server_name localhost ;
     location / {
    index index.html index.htm;
    }
    server {
    listen 443 ssl;
    server_name localhost;
    root html;
    index index.html index.htm;
    ssl_certificate cert/domain name.pem;   #将domain name.pem替换成您证书的文件名。
    ssl_certificate_key cert/domain name.key;   #将domain name.key替换成您证书的密钥文件名。
    ssl_session_timeout 5m;
    ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    ssl_prefer_server_ciphers on;
    location / {
    index index.html index.htm;
    }
    ```

3.  保存vhost.conf或\*.conf文件后退出。

4.  设置HTTP请求自动跳转HTTPS。

    在Web目录下打开.htaccess文件（如果没有，需新建该文件），添加以下rewrite语句，实现HTTP访问自动跳转到HTTPS页面。

    ```
    RewriteEngine On
    RewriteCond %{HTTP:From-Https} !^on$ [NC]
    RewriteCond %{HTTP_HOST} ^(www.)?yourdomain.com$ [NC]                # 将yourdomain.com修改为您证书绑定的域名，例如：example.com。
    RewriteRule ^(.*)$ https://www.yourdomain.com/$1 [R=301,L]           # 将yourdomain.com修改为您证书绑定的域名，例如：example.com。
    ```

5.  重启虚拟主机。


**说明：** 证书安装成功后，需要在虚拟主机上配置伪静态规则，您的网站才能全站都支持HTTPS，否则只有网站的主页支持HTTPS，网站的子目录将不支持HTTPS。

## 后续操作

证书安装完成后，您可通过登录证书的绑定域名验证该证书是否安装成功。

```
https://domain name   #domain name替换成证书绑定的域名。
```

如果网页地址栏出现小锁标志，表示证书安装成功。

DV SSL、OV SSL数字证书部署在服务器上后，您的浏览器访问网站时，展示以下效果：

![DV/OV证书安装效果图](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9328588951/p108043.png)

证书安装完成后，异常现象的处理方法，请参见下表：

|异常现象|可能原因|处理方法|
|----|----|----|
|通过HTTPS无法正常访问您的网站。|您安装证书的Nginx服务器443端口未开启或被其他工具拦截。|如果您使用的是阿里云ECS服务器，请前往[ECS管理控制台](https://ecs.console.aliyun.com)的**安全组**页面配置放行443端口。|
|您的网站显示“您与网站之间的链接未完全安全”。|您的网站代码中调用的是HTTP协议。|需要您在网站代码中把HTTP协议修改为HTTPS协议。**说明：** 不同网站代码的实现逻辑可能存在差异，请您根据具体情况进行修改。 |
|您的网站显示“该网站未根据工信部相关法律进行备案”。|-   您的网站未完成备案，未在接入商完成备案接入。
-   您的网站内容与备案信息不符、备案信息不准确、网站存在不适宜传播的内容等。

|如果您使用的是阿里云备案系统，请前往[阿里云备案系统](https://beian.aliyun.com/order/index)进行网站备案。|

## 相关文档

-   [在Tomcat服务器上安装SSL证书](/cn.zh-CN/证书下载和安装/Tomcat服务器安装SSL证书/安装PFX格式证书.md)
-   [在Apache服务器上安装SSL证书](/cn.zh-CN/证书下载和安装/在Apache服务器上安装SSL证书.md)
-   [Ubuntu系统Apache 2部署SSL证书](/cn.zh-CN/最佳实践/Ubuntu系统Apache 2部署SSL证书.md)
-   [我获取到的数字证书如何配置在自己的Apache中？]()
-   [在IIS服务器上安装SSL证书](/cn.zh-CN/证书下载和安装/在IIS服务器上安装SSL证书.md)
-   [CentOS系统Tomcat 8.5或9部署SSL证书](/cn.zh-CN/最佳实践/CentOS系统Tomcat 8.5或9部署SSL证书.md)
-   [在Jetty服务器上安装SSL证书](/cn.zh-CN/证书下载和安装/在Jetty服务器上安装SSL证书.md)

