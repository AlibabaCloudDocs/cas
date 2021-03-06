# SSL证书安装指南

通过SSL证书服务购买并签发证书后，您可以通过SSL证书控制台将已签发的证书下载到本地，并根据需要将证书安装到要使用证书的环境。阿里云SSL证书适用于安装到Web服务器、部署到支持的阿里云产品。

已通过SSL证书服务购买并签发证书。相关操作，请参见[购买SSL证书实例](/intl.zh-CN/证书购买/购买SSL证书实例.md)、[提交证书申请](/intl.zh-CN/证书申请/提交证书申请.md)。

## 证书安装场景介绍

|场景|说明|操作流程概览|
|--|--|------|
|安装到Web服务器|表示在提供Web服务的服务器上配置SSL证书，并开启HTTPS监听，实现客户端与服务端之间的HTTPS通信。不同类型的Web服务器支持配置的证书格式不同。为了便于您安装证书，SSL证书服务提供了适用于各种主流Web服务器（例如，Nginx、Apache Tomcat、Apache（httpd）、Internet Information Services）的证书压缩包，供您直接下载使用（无需手动转换证书格式）。

|1.  通过[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)下载已签发的证书到本地。

您可以根据Web服务器的类型，下载对应格式的证书文件。具体操作，请参见[下载证书到本地](#section_cjh_359_s85)。

2.  将下载的证书文件上传到Web服务器，并修改服务器的相关配置，开启HTTPS监听。

不同Web服务器需要修改的配置不同，SSL证书服务提供了主流Web服务器安装SSL证书的方法介绍。更多信息，请参见[在服务器上安装证书](#section_ri1_ayr_evy)。 |
|部署到阿里云产品|表示通过SSL证书控制台，将SSL证书快速应用到阿里云产品的指定资源上，简化证书配置操作。目前只有以下阿里云产品支持通过SSL证书服务部署证书：Web应用防火墙（WAF）、对象存储OSS、传统型负载均衡CLB（原SLB）、应用型负载均衡ALB、CDN、安全加速、全站加速、视频直播、DDoS高防。更多信息，请参见[支持一键部署证书的阿里云产品](/intl.zh-CN/产品简介/什么是SSL证书服务.md)。

|通过[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)的**部署**操作，将已签发的证书一键应用到指定的阿里云资源上。具体操作，请参见[部署证书到阿里云产品](/intl.zh-CN/证书安装/部署证书到阿里云产品.md)。|

## 下载证书到本地

如果您已经通过SSL证书服务购买并签发了SSL证书，可以执行以下步骤，将已签发的阿里云SSL证书下载到本地。

**说明：** 为了保证数据安全性，您上传到SSL证书服务进行统一管理的第三方证书不支持下载。

1.  登录[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)。

2.  在证书列表，定位到要下载的证书，单击**操作**列下的**下载**。

    **说明：** 只有状态为**已签发**、**即将过期**、**已过期**的证书支持**下载**操作，否则证书**操作**列下不会显示**下载**按钮。

3.  在**证书下载**面板，下载适用于您的Web服务器的证书。

    SSL证书服务已经将您的证书自动转换成适用于不同Web服务器的格式并压缩，您只需根据服务器类型，单击对应的**下载**按钮，即可将满足该类型服务器配置需求的证书压缩包下载到本地。

    ![证书下载 ](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5049571261/p276585.png)

    证书下载示例：

    -   如果您的Web服务器类型是Apache Tomcat（支持配置PFX格式、JKS格式的证书），根据要配置的证书类型进行操作：
        -   单击**Tomcat**后的**下载**，下载PFX格式的证书压缩包。
        -   单击**JKS**后的**下载**，下载JKS格式的证书压缩包。
    -   如果您的Web服务器类型是Apache（httpd）、Nginx、Internet Information Services（IIS），分别单击**Apache**、**Nginx**、**IIS**后的**下载**。
    -   如果您的Web服务器类型不在Apache Tomcat、Apache（httpd）、Nginx、IIS范围，单击**其他**后的**下载**。
    -   如果您需要将证书安装到阿里云产品上，推荐您使用[证书部署功能](/intl.zh-CN/证书安装/部署证书到阿里云产品.md)。如果要安装证书的阿里云产品暂不支持证书部署，建议您下载适用于Nginx服务器的证书压缩包（即单击**Nginx**后的**下载**）。
    -   如果您需要在App、Java等客户端上安装根证书，单击**根证书下载**后的**下载**。

        **说明：** 对于通过客户端浏览器访问的Web服务，无需关注根证书，因为根证书已经内置在客户端浏览器。

    完成下载后，证书压缩包将会被下载到当前浏览器的默认下载目录。您可以在下载目录中查看已下载的证书压缩包，并解压获得对应的证书文件。


## 在服务器上安装证书

通过SSL证书控制台下载证书到本地后，您还需要将已下载的证书上传到Web服务器并修改服务器的相关配置，才能使SSL证书生效。

不同Web服务器安装SSL证书的具体操作不同。以下内容介绍了在主流Web服务器上安装SSL证书的方法，供您参考。

|Web服务器类型|证书安装方法|
|--------|------|
|Nginx、Tengine|[在Nginx（或Tengine）服务器上安装证书](/intl.zh-CN/证书安装/安装证书到服务器/在Nginx（或Tengine）服务器上安装证书.md)|
|Apache Tomcat 7（及以下版本）|-   [安装PFX格式证书](/intl.zh-CN/证书安装/安装证书到服务器/Tomcat服务器安装SSL证书/安装PFX格式证书.md)
-   [安装JKS格式证书](/intl.zh-CN/证书安装/安装证书到服务器/Tomcat服务器安装SSL证书/安装JKS格式证书.md) |
|Apache Tomcat 8（及以上版本）|[CentOS系统Tomcat 8.5或9部署SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/CentOS系统Tomcat 8.5或9部署SSL证书.md)|
|Apache（httpd）|[在Apache服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在Apache服务器上安装SSL证书.md)|
|Apache 2|[Ubuntu系统Apache 2部署SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/Ubuntu系统Apache 2部署SSL证书.md)|
|IIS|[在IIS服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在IIS服务器上安装SSL证书.md)|
|Jetty|[在Jetty服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在Jetty服务器上安装SSL证书.md)|
|JBoss|[在JBoss服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在JBoss服务器上安装SSL证书.md)|
|GlassFish|[在GlassFish服务器上安装SSL证书](/intl.zh-CN/证书安装/安装证书到服务器/在GlassFish服务器上安装SSL证书.md)|

