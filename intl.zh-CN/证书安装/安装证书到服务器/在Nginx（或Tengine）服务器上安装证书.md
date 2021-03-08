---
keyword: [SSL证书, Nginx服务器, Tengine服务器, 支持HTTPS]
---

# 在Nginx（或Tengine）服务器上安装证书

通过SSL证书服务购买和签发证书后，您可以将已签发的证书下载并安装到Nginx（或Tengine）服务器上。本文介绍了下载SSL证书并在Nginx（或Tengine）服务器上安装证书的具体操作。

-   已经通过SSL证书服务完成证书签发。更多信息，请参见[提交证书申请](/intl.zh-CN/证书申请/提交证书申请.md)。
-   已准备好远程登录工具（例如PuTTY、Xshell），用于登录您的Web服务器。

本文以CentOS 8操作系统、Nginx 1.14.1服务器系统为例进行说明。由于服务器系统版本不同，您在操作过程中使用的命令可能会略有区别。

本文中出现证书文件名称的地方，统一使用**cert-file-name**为例进行描述。例如，本文中用到的证书文件为cert-file-name.pem、证书密钥文件为cert-file-name.key。

**说明：** 您在实际操作过程中，需要根据示例代码中的提示，将**cert-file-name**替换成您的证书文件的名称。关于如何获取证书文件的名称，请参见[下载证书到本地](#step_g2p_wai_ral)。

## 步骤1：下载证书到本地

1.  登录[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)。

2.  在**概览**页面，单击证书列表上方的证书状态下拉列表，并选择**已签发**。

    该操作将会筛选出所有已经通过CA机构签发的证书。

3.  定位到要下载的证书，单击操作列下的**下载**。

4.  在**证书下载**页面，定位到**Nginx**服务器，单击操作列下的**下载**。

    该操作会将Nginx服务器证书压缩包下载到本地，并保存在浏览器的默认下载位置。

5.  打开浏览器的默认下载位置，解压已下载的Nginx证书压缩包文件。

    解压后您将会获得以下文件：

    ![证书文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1690497061/p33690.png)

    -   PEM格式的证书文件。

        **说明：** 在后续安装证书的操作中，您必须使用真实的证书文件名称替换示例代码中的`cert-file-name`。

        PEM格式的证书文件是采用Base64编码的文本文件，您可以根据需要将证书文件修改成其他格式。关于证书格式的更多信息，请参见[主流数字证书都有哪些格式](/intl.zh-CN/产品简介/常见问题/主流数字证书都有哪些格式？.md)。

    -   KEY格式的证书密钥文件。

        **说明：** 如果您在申请证书时将**CSR生成方式**设置为**手动填写**，则下载的证书文件压缩包中不会包含KEY文件，您需要手动创建证书密钥文件。

        ![CSR生成方式](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1690497061/p199706.png)

6.  在Nginx服务器上安装证书。

    根据您是否使用独立的Nginx服务器，安装证书的操作不同：

    -   如果您使用的是独立服务器，请参见[步骤2：（可选）在Nginx独立服务器上安装证书](#section_ydh_4qb_1gb)。
    -   如果您使用的是虚拟主机，请参见[步骤2：（可选）为Nginx虚拟主机配置SSL证书](#section_wy0_022_q1s)。

## 步骤2：（可选）在Nginx独立服务器上安装证书

1.  登录Nginx服务器。

    例如，您可以使用远程登录工具（例如，PuTTY、Xshell）登录服务器。

2.  执行以下命令，在Nginx安装目录（默认为/usr/local/nginx/conf）下创建一个用于存放证书的目录（命名为cert）。

    ```
    cd /usr/local/nginx/conf  #进入Nginx默认安装目录。如果您修改过默认安装目录，请根据实际配置进行调整。
    mkdir cert  #创建证书目录，命名为cert。
    ```

3.  使用远程登录工具（例如，PuTTY、Xshell）附带的本地文件上传功能，将本地证书文件和密钥文件上传到Nginx服务器的证书目录（示例中为/usr/local/nginx/conf/cert）。

    **说明：** 如果您在申请证书时将**CSR生成方式**设置为**手动填写**，请将您手动创建的证书密钥文件上传到/usr/local/nginx/conf/cert目录。

4.  编辑Nginx配置文件（nginx.conf），修改与证书相关的配置内容。

    1.  执行以下命令，打开配置文件。

        使用示例命令前，请注意：nginx.conf默认保存在/usr/local/nginx/conf目录下。如果您修改过nginx.conf的位置，请将`/usr/local/nginx/conf/nginx.conf`替换成修改后的位置。

        ```
        vim /usr/local/nginx/conf/nginx.conf
        ```

    2.  按i键进入编辑模式。

    3.  在配置文件中定位到HTTP协议代码片段（`http{}`），并在HTTP协议代码里面添加以下server配置（如果server配置已存在，按照以下注释内容修改相应配置即可）。

        使用示例代码前，请注意替换以下内容：

        -   `yourdomain.com`：替换成证书绑定的域名。

            如果您购买的是单域名证书，需要修改为单域名（例如`www.aliyun.com`）；如果您购买的是通配符域名证书，则需要修改为通配符域名（例如`*.aliyun.com`）。

        -   `cert-file-name.pem`：替换成您在步骤3上传的证书文件的名称。
        -   `cert-file-name.key`：替换成您在步骤3上传的证书密钥文件的名称。
        ```
        #以下属性中，以ssl开头的属性表示与证书配置有关。
        server {
            listen 443 ssl;
            #配置HTTPS的默认访问端口为443。
            #如果未在此处配置HTTPS的默认访问端口，可能会造成Nginx无法启动。
            #如果您使用Nginx 1.15.0及以上版本，请使用listen 443 ssl代替listen 443和ssl on。
            server_name yourdomain.com; #需要将yourdomain.com替换成证书绑定的域名。
            root html;
            index index.html index.htm;
            ssl_certificate cert/cert-file-name.pem;  #需要将cert-file-name.pem替换成已上传的证书文件的名称。
            ssl_certificate_key cert/cert-file-name.key; #需要将cert-file-name.key替换成已上传的证书密钥文件的名称。
            ssl_session_timeout 5m;
            ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
            #表示使用的加密套件的类型。
            ssl_protocols TLSv1 TLSv1.1 TLSv1.2; #表示使用的TLS协议的类型。
            ssl_prefer_server_ciphers on;
            location / {
                root html;  #站点目录。
                index index.html index.htm;
            }
        }
        ```

    4.  设置HTTP请求自动跳转HTTPS。

        如果您希望所有的HTTP访问自动跳转到HTTPS页面，则可以在需要跳转的HTTP站点下添加以下`rewrite`语句。

        使用示例代码前，请注意将`yourdomain.com`替换成证书绑定的域名。

        ```
        server {
            listen 80;
            server_name yourdomain.com; #需要将yourdomain.com替换成证书绑定的域名。
            rewrite ^(.*)$ https://$host$1; #将所有HTTP请求通过rewrite指令重定向到HTTPS。
            location / {
                index index.html index.htm;
            }
        }
        ```

        **警告：** 如果您使用的是阿里云ECS服务器，必须在[ECS管理控制台](https://ecs.console.aliyun.com)的**安全组**页面，配置放行80端口和443端口，否则网站访问可能出现异常。关于如何配置安全组，请参见[添加安全组规则](/intl.zh-CN/安全/安全组/添加安全组规则.md)。

    5.  修改完成后，按Esc键、输入:wq！并按Enter键，保存修改后的配置文件并退出编辑模式。

5.  执行以下命令，重启Nginx服务。

    ```
    cd /usr/local/nginx/sbin  #进入Nginx服务的可执行目录。
    ./nginx -s reload  #重新载入配置文件。
    ```

    如果重启Nginx服务时收到报错，您可以使用以下方法进行排查：

    -   收到`the "ssl" parameter requires ngx_http_ssl_module`报错：您需要重新编译Nginx并在编译安装的时候加上`--with-http_ssl_module`配置。
    -   收到`"/cert/3970497_pic.certificatestests.com.pem":BIO_new_file() failed (SSL: error:02001002:system library:fopen:No such file or directory:fopen('/cert/3970497_pic.certificatestests.com.pem','r') error:2006D080:BIO routines:BIO_new_file:no such file)`报错：您需要去掉证书相对路径最前面的`/`。例如，您需要去掉`/cert/cert-file-name.pem`最前面的`/`，使用正确的相对路径`cert/cert-file-name.pem`。
6.  验证证书是否安装成功。

    具体操作，请参见[步骤3：验证是否安装成功](#section_liy_o8x_gug)。


## 步骤2：（可选）为Nginx虚拟主机配置SSL证书

1.  登录您的虚拟机。

2.  在Web目录下创建cert目录，并将下载的证书文件和密钥文件拷贝到cert目录中。

3.  打开虚拟主机配置文件，将以下内容复制粘贴到文件末尾。

    **说明：** 不同服务器系统的虚拟主机配置文件不同，例如，Nginx服务器默认是\*.conf、Apache服务器默认是vhosts.conf等。关于虚拟主机配置文件的具体路径，请参照服务器使用说明中关于开启虚拟主机方法的介绍。

    ```
    server {
        listen 80;
        server_name localhost;
        location / {
            index index.html index.htm;
        }
    }
    server {
        listen 443 ssl;
        server_name localhost;
        root html;
        index index.html index.htm;
        ssl_certificate cert/cert-file-name.pem;   #需要将cert-file-name.pem替换成已上传的证书文件的名称。
        ssl_certificate_key cert/cert-file-name.key;   #需要将cert-file-name.key替换已上传的证书密钥文件的名称。
        ssl_session_timeout 5m;
        ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_prefer_server_ciphers on;
        location / {
            index index.html index.htm;
        }
    }
    ```

4.  保存vhost.conf或\*.conf文件并退出。

5.  设置HTTP请求自动跳转HTTPS。

    如果您希望所有的HTTP访问自动跳转到HTTPS页面，则可以在Web目录下打开.htaccess文件（如果没有，需新建该文件），并添加以下rewrite语句。

    ```
    RewriteEngine On
    RewriteCond %{HTTP:From-Https} !^on$ [NC]
    RewriteCond %{HTTP_HOST} ^(www.)?yourdomain.com$ [NC]   #需要将yourdomain.com替换成证书绑定的域名。
    RewriteRule ^(.*)$ https://www.yourdomain.com/$1 [R=301,L]   #需要将yourdomain.com替换成证书绑定的域名。
    ```

6.  重启虚拟主机。

    **说明：** 证书安装成功后，您需要在虚拟主机上配置伪静态规则，这样您的网站才能全站都支持HTTPS，否则只有网站的主页支持HTTPS，网站的子目录将不支持HTTPS。

7.  验证证书是否安装成功。

    具体操作，请参见[步骤3：验证是否安装成功](#section_liy_o8x_gug)。


## 步骤3：验证是否安装成功

证书安装完成后，您可通过访问证书的绑定域名验证该证书是否安装成功。

```
https://yourdomain.com   #需要将yourdomain.com替换成证书绑定的域名。
```

如果网页地址栏出现小锁标志，表示证书已经安装成功。

如果验证时出现访问异常，请参照下表进行排查。

|异常现象|可能原因|处理方法|
|----|----|----|
|通过HTTPS无法正常访问您的网站。|安装证书的Nginx服务器的443端口未开放或被其他工具拦截。|-   如果您使用的是阿里云ECS服务器，请前往[ECS管理控制台](https://ecs.console.aliyun.com)的**安全组**页面，配置开放443端口。

关于如何配置安全组，请参见[添加安全组规则](/intl.zh-CN/安全/安全组/添加安全组规则.md)。

-   如果您使用的不是阿里云ECS服务器，请参照对应的服务器安全设置指南，配置开放服务器的443端口。 |
|收到网站提示“您与网站之间的连接未完全安全”。|您的网站代码中调用的是HTTP协议。|您需要在网站代码中把HTTP协议修改为HTTPS协议。**说明：** 不同网站代码的实现逻辑可能存在差异，请您根据具体情况进行修改。如果需要更多支持，请提交[工单](https://ticket-intl.console.aliyun.com/#/ticket/add/?productId=80)。 |

## 相关文档

-   [在Tomcat服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/Tomcat服务器安装SSL证书/安装PFX格式证书.md)
-   [在Apache服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在Apache服务器上安装SSL证书.md)
-   [Ubuntu系统Apache 2部署SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/Ubuntu系统Apache 2部署SSL证书.md)
-   [我获取到的数字证书如何配置在自己的Apache中？]()
-   [在IIS服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在IIS服务器上安装SSL证书.md)
-   [CentOS系统Tomcat 8.5或9部署SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/CentOS系统Tomcat 8.5或9部署SSL证书.md)
-   [在Jetty服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在Jetty服务器上安装SSL证书.md)

