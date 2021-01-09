---
keyword: [阿里云SSL证书, IIS服务器, 支持HTTPS]
---

# 在IIS服务器上安装SSL证书

阿里云SSL证书服务支持下载SSL证书并安装到IIS服务器上，从而使您的IIS服务器支持HTTPS安全访问。本文介绍了在IIS服务器上安装证书的具体操作。

-   已安装IIS服务器，且您的IIS服务器上已经开启了443端口（HTTPS服务的默认端口）。
-   已安装OpenSSL工具。
-   已下载IIS服务器所需要的证书文件。有关证书下载的具体操作，请参见[下载证书](/intl.zh-CN/证书安装/下载证书.md)。

    **说明：**

    申请证书时需要选择**系统自动创建CSR**，如果选择**手动创建CSR**，则不会生成证书文件。您需要选择**其他**服务器下载.crt证书文件后，使用openssl命令将.crt文件的证书转换成.pfx格式。


## 操作步骤

1.  在SSL证书页面，定位到需要下载的证书实例并单击证书卡片右下角的**下载**

    ![下载](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2256669951/p39167.jpg)

2.  定位到**IIS**服务器类型并单击右侧**操作**栏的**下载**将IIS版证书压缩包下载到本地。

    ![证书下载页面](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2405359851/p101231.png)

3.  解压已下载保存到本地的IIS证书文件。您将看到文件中有一个证书文件（以.pfx为后缀或文件类型）和一个密钥文件（以.txt为后缀或文件类型）。

    ![证书文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2405359851/p33691.png)

    **说明：** 每次下载证书都会产生新的密码，该密码仅匹配本次下载的证书。如果需要更新证书文件，同时也要更新匹配的密码文件。

4.  在**IIS服务器控制台**中导入您解压的IIS证书文件。

    1.  在安装IIS服务器的Windows系统中，单击**开始** \> **运行** \> **MMC**打开控制台。

    2.  单击**文件** \> **添加/删除管理单元**打开**添加/删除管理单元**对话框。

        ![添加/删除管理单元](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2405359851/p33702.png)

    3.  在**可用的管理单元**列表中选择**证书**，单击**添加**选择**计算机账户**。然后单击**下一步**完成**本地计算机（运行此控制台的计算机）**的选择。

        ![添加或删除管理单元界面](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2405359851/p101260.png)

    4.  在控制台左侧导航栏单击**控制台根节点**下的**证书**打开证书树形列表。

        ![打开证书树形列表](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2405359851/p33705.png)

    5.  在**个人**右键菜单中选择**所有任务** \> **导入**，打开**证书导入向导**对话框，并单击**下一步**。

        ![打开证书导入向导](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3405359851/p33706.png)

    6.  在要导入的文件页面单击**浏览**导入下载的PFX格式证书文件，并单击**下一步**。

        ![导入证书](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3405359851/p33837.png)

        **说明：** 在导入证书文件时，**文件名**右侧文件类型列表中请选择**所有文件**类型。

    7.  输入证书密钥文件里的密码，并单击**下一步**。

        您可在下载的IIS证书文件中打开pfx-password .txt文件查看证书密码。

        ![输入证书秘钥](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3405359851/p33838.png)

    8.  选择**根据证书类型，自动选择证书存储**并单击**下一步**完成证书的导入。

        ![选择证书存储](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3405359851/p33839.png)

5.  分配服务器证书。

    1.  打开IIS 8.0 管理器面板，定位到待安装证书的站点，单击**绑定**。

    2.  在**网站绑定**对话框中单击**添加** \> **选择https类型** \> **端口选择443** \> **导入的IIS证书名称** \> **确定**。

        **说明：** SSL缺省端口为443端口，请不要修改。如果您使用其他端口（例如8443端口），则访问网站时必须输入`https://www.domain.com:8443`。


## 后续操作

证书安装完成后，您可通过访问证书的绑定域名验证该证书是否安装成功。

```
https://yourdomain.com   #需要将yourdomain.com替换成证书绑定的域名。
```

如果网页地址栏出现小锁标志，表示证书已经安装成功。

证书安装完成后，如果网站无法通过HTTPS正常访问，需确认您安装证书的服务器443端口是否已开启或被其他工具拦截。如果您使用的是阿里云ECS服务器，请前往ECS控制台**安全组**页面配置放行443端口。

## 相关文档

-   [在Tomcat服务器上安装SSL证书](/intl.zh-CN/证书安装/Tomcat服务器安装SSL证书/安装PFX格式证书.md)
-   [在Apache服务器上安装SSL证书](/intl.zh-CN/证书安装/在Apache服务器上安装SSL证书.md)
-   [Ubuntu系统Apache 2部署SSL证书](/intl.zh-CN/最佳实践/Ubuntu系统Apache 2部署SSL证书.md)
-   [我获取到的数字证书如何配置在自己的Apache中？]()
-   [在Nginx（或Tengine）服务器上安装证书](/intl.zh-CN/证书安装/在Nginx（或Tengine）服务器上安装证书.md)
-   [CentOS系统Tomcat 8.5或9部署SSL证书](/intl.zh-CN/最佳实践/CentOS系统Tomcat 8.5或9部署SSL证书.md)
-   [在Jetty服务器上安装SSL证书](/intl.zh-CN/证书安装/在Jetty服务器上安装SSL证书.md)

