# Ubuntu系统Apache 2部署SSL证书

本文档为您介绍了如何在Ubuntu系统以及Apache2中安装阿里云SSL证书。

## 环境准备

操作系统：Ubuntu

Web服务器：Apache 2

## 前提条件

-   已从[SSL证书控制台](https://yundunnext.console.aliyun.com/?spm=5176.2020520155.aliyun_sidebar.30.25af2a528ujbXD&p=cas#/overview/cn-hangzhou)下载Apache服务器证书。
-   已从[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas#/overview/cn-hangzhou)下载Apache服务器证书。
-   已安装Open SSL。

## 操作步骤

1.  运行以下命令在apache2目录下创建ssl目录。

    ```
    mkdir /etc/apache2/ssl
    ```

2.  运行以下命令将下载的阿里云证书文件复制到ssl目录中。

    ```
    cp -r YourDomainName_public.crt /etc/apache2/ssl
    ```

    ```
    cp -r YourDomainName_chain.crt /etc/apache2/ssl
    ```

    ```
    cp -r YourDomainName.key /etc/apache2/ssl
    ```

3.  运行以下命令启用SSL模块。

    ```
    sudo a2enmod ssl
    ```

    ![启用SSL模块](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6586939751/p36989.png)

    SSL模块启用后可执行`ls /etc/apache2/sites-available`查看目录下生成的default-ssl.conf文件。

    **说明：** 443端口是网络浏览端口，主要用于HTTPS服务。SSL模块启用后会自动放行443端口。若443端口未自动放行，可执行`vi /etc/apache2/ports.conf`并添加`Listen 443`手动放行。

4.  运行以下命令修改SSL配置文件default-ssl.conf。

    ```
    vi /etc/apache2/sites-available/default-ssl.conf
    ```

    在default-ssl.conf文件中找到以下参数进行修改后保存并退出。

    ```
    <IfModules mod_ssl.c>
    <VirtualHost *:443>  
    ServerName   #修改为证书绑定的域名www.YourDomainName.com。
    SSLCertificateFile /etc/apache2/ssl/www.YourDomainName_public.crt   #将/etc/apache2/ssl/www.YourDomainName.com_public.crt替换为证书文件路径+证书文件名。
    SSLCertificateKeyFile /etc/ssl/apache2/www.YourDomainName.com.key   #将/etc/apache2/ssl/www.YourDomainName.com.key替换为证书密钥文件路径+证书密钥文件名。
    SSLCertificateChainFile /etc/apache2/ssl/www.YourDomainName.com_chain.crt  #将/etc/apache2/ssl/www.YourDomainName.com_chain.crt替换为证书链文件路径+证书链文件名。
    						
    ```

    ![修改SSL配置文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6586939751/p36991.png)

    /sites-available：该目录存放的是可用的虚拟主机；/sites-enabled：该目录存放的是已经启用的虚拟主机。

    **说明：** default-ssl.conf文件可能存放在/etc/apache2/sites-available或/etc/apache2/sites-enabled目录中。

5.  运行以下命令把default-ssl.conf映射至/etc/apache2/sites-enabled文件夹中建立软链接、实现二者之间的自动关联。

    ```
    sudo ln -s /etc/apache2/sites-available/default-ssl.conf /etc/apache2/sites-enabled/001-ssl.conf
    ```

6.  运行以下命令重新加载Apache 2配置文件。

    ```
    sudo /etc/init.d/apache2 force-reload
    ```

    ![重新加载Apache 2配置文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6586939751/p36992.png)

7.  运行以下命令重启Apache 2服务。

    ```
    sudo /etc/init.d/apache2 restart
    ```

    ![重启Apache 2服务](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7586939751/p36993.png)


## 后续操作

Apache 2服务重启成功后，您可在浏览器中输入https://www.YourDomainName.com验证证书安装结果。浏览器地址栏显示绿色的小锁标识说明证书安装成功。

安装证书相关文档：

-   [在Tomcat服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/Tomcat服务器安装SSL证书/安装PFX格式证书.md)
-   [在Apache服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在Apache服务器上安装SSL证书.md)
-   [我获取到的数字证书如何配置在自己的Apache中？]()
-   [在Nginx（或Tengine）服务器上安装证书](/intl.zh-CN/证书安装/安装证书到服务器/在Nginx（或Tengine）服务器上安装证书.md)
-   [在IIS服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在IIS服务器上安装SSL证书.md)
-   [CentOS系统Tomcat 8.5或9部署SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/CentOS系统Tomcat 8.5或9部署SSL证书.md)
-   [在Jetty服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在Jetty服务器上安装SSL证书.md)

