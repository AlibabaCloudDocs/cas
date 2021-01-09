---
keyword: [阿里云SSL证书, Apache服务器, 支持HTTPS, httpd-ssl.conf]
---

# 在Apache服务器上安装SSL证书

阿里云SSL证书服务支持下载证书安装到Apache服务器，从而使Apache服务器支持HTTPS安全访问。本文介绍了证书安装的具体操作。

-   您的Apache服务器上已经开启了443端口（HTTPS服务的默认端口）。
-   您的Apache服务器上已安装了mod\_ssl.so模块（启用SSL功能）。
-   本文档证书名称以**domain name**为示例，例如：证书文件名称为**domain name\_public.crt**，证书链文件名称为**domain name\_chain.crt**，证书密钥文件名称为**domain name.key**。
-   申请证书时如果未选择**系统自动创建CSR**，证书下载压缩包中将不包含.key文件。

**说明：** .crt扩展名的证书文件采用Base64-encoded的PEM格式文本文件，可根据需要修改成.pem等扩展名。 证书格式详细内容，请参见[主流数字证书都有哪些格式？](/intl.zh-CN/产品简介/常见问题/主流数字证书都有哪些格式？.md)

## 操作步骤

1.  解压已下载保存到本地的Apache证书文件。

    解压后的文件夹中有3个文件：

    ![证书文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1154972951/p33689.png)

    -   证书文件：以.crt为后缀或文件类型。
    -   证书链文件：以.crt为后缀或文件类型。
    -   密钥文件：以.key为后缀或文件类型。
2.  在**Apache**安装目录中新建cert目录，并将解压的Apache证书、证书链文件和密钥文件拷贝到cert目录中。如果需要安装多个证书，需在**Apache**目录中新建对应数量的**cert**目录，用于存放不同的证书 。

    **说明：** 如果申请证书时选择了**手动创建CSR文件**，请将手动生成创建的密钥文件拷贝到**cert目录**中并命名为domain name.key。

3.  修改httpd.conf配置文件。

    1.  在Apache安装目录下，打开Apache/conf/httpd.conf文件，并找到以下参数，按照下文中注释内容进行配置。

        ```
        #LoadModule ssl_module modules/mod_ssl.so  #删除行首的配置语句注释符号“#”加载mod_ssl.so模块启用SSL服务，Apache默认是不启用该模块的。
        #Include conf/extra/httpd-ssl.conf  #删除行首的配置语句注释符号“#”。                 
        ```

        **说明：** 如果您在httpd.conf文件中没有找到以上配置语句，请确认您的Apache服务器中是否已经安装mod\_ssl.so模块。可执行`yum install -y mod_ssl`命令安装mod\_ssl模块。

    2.  保存httpd.conf文件并退出。

4.  修改httpd-ssl.conf配置文件。

    1.  打开Apache/conf/extra/httpd-ssl.conf文件并找到以下参数，按照下文中注释内容进行配置。

        **说明：** 根据操作系统的不同，http-ssl.conf文件也可能存放在conf.d/ssl.conf目录中。

        ```
        <VirtualHost *:443>     
            ServerName   #修改为申请证书时绑定的域名www.YourDomainName1.com。                    
            DocumentRoot  /data/www/hbappserver/public          
            SSLEngine on   
            SSLProtocol all -SSLv2 -SSLv3 # 添加SSL协议支持协议，去掉不安全的协议。
            SSLCipherSuite HIGH:!RC4:!MD5:!aNULL:!eNULL:!NULL:!DH:!EDH:!EXP:+MEDIUM   # 修改加密套件。
            SSLHonorCipherOrder on
            SSLCertificateFile cert/domain name1_public.crt   # 将domain name1_public.crt替换成您证书文件名。
            SSLCertificateKeyFile cert/domain name1.key   # 将domain name1.key替换成您证书的密钥文件名。
            SSLCertificateChainFile cert/domain name1_chain.crt  # 将domain name1_chain.crt替换成您证书的密钥文件名；证书链开头如果有#字符，请删除。
        </VirtualHost>
        
        #如果证书包含多个域名，复制以上参数，并将ServerName替换成第二个域名。 
        <VirtualHost *:443>     
            ServerName   #修改为申请证书时绑定的第二个域名www.YourDomainName2.com。                    
            DocumentRoot  /data/www/hbappserver/public          
            SSLEngine on   
            SSLProtocol all -SSLv2 -SSLv3 # 添加SSL协议支持协议，去掉不安全的协议。
            SSLCipherSuite HIGH:!RC4:!MD5:!aNULL:!eNULL:!NULL:!DH:!EDH:!EXP:+MEDIUM   # 修改加密套件。
            SSLHonorCipherOrder on
            SSLCertificateFile cert/domain name2_public.crt   # 将domain name2替换成您申请证书时的第二个域名。
            SSLCertificateKeyFile cert/domain name2.key   # 将domain name2替换成您申请证书时的第二个域名。
            SSLCertificateChainFile cert/domain name2_chain.crt  # 将domain name2替换成您申请证书时的第二个域名；证书链开头如果有#字符，请删除。
        </VirtualHost>
        ```

        **说明：** 需注意您的浏览器版本是否支持SNI功能。如果不支持，多域名证书配置将无法生效。

    2.  保存httpd-ssl.conf文件并退出。

5.  重启Apache服务器使SSL配置生效。

    在Apache的bin目录下执行以下命令：

    1.  停止Apache服务。

        ```
        apachectl -k stop
        ```

    2.  开启Apache服务。

        ```
        apachectl -k start
        ```

6.  修改httpd.conf文件，设置HTTP请求自动跳转HTTPS。

    在httpd.conf文件中的`<VirtualHost *:80> </VirtualHost>`中间，添加以下重定向代码。

    ```
    RewriteEngine on
    RewriteCond %{SERVER_PORT} !^443$
    RewriteRule ^(.*)$ https://%{SERVER_NAME}$1 [L,R]
    ```


## 后续操作

证书安装完成后，您可通过访问证书的绑定域名验证该证书是否安装成功。

```
https://yourdomain.com   #需要将yourdomain.com替换成证书绑定的域名。
```

如果网页地址栏出现小锁标志，表示证书已经安装成功。

证书安装完成后，如果网站无法通过HTTPS正常访问，需确认您安装证书的服务器443端口是否已开启或被其他工具拦截。如果您使用的是阿里云ECS服务器，请前往ECS控制台**安全组**页面配置放行443端口。

## 相关文档

[在Tomcat服务器上安装SSL证书](/intl.zh-CN/证书安装/Tomcat服务器安装SSL证书/安装PFX格式证书.md)

[Ubuntu系统Apache 2部署SSL证书](/intl.zh-CN/最佳实践/Ubuntu系统Apache 2部署SSL证书.md)

[我获取到的数字证书如何配置在自己的Apache中？]()

[在Nginx（或Tengine）服务器上安装证书](/intl.zh-CN/证书安装/在Nginx（或Tengine）服务器上安装证书.md)

[在IIS服务器上安装SSL证书](/intl.zh-CN/证书安装/在IIS服务器上安装SSL证书.md)

[CentOS系统Tomcat 8.5或9部署SSL证书](/intl.zh-CN/最佳实践/CentOS系统Tomcat 8.5或9部署SSL证书.md)

[在Jetty服务器上安装SSL证书](/intl.zh-CN/证书安装/在Jetty服务器上安装SSL证书.md)

