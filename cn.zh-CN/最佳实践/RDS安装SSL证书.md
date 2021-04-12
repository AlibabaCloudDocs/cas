# RDS安装SSL证书

RDS提供SSL加密功能。您可以在RDS控制台开启SSL设置、下载SSL证书并将证书安装到您的数据库客户端中。本文介绍了如何在RDS上安装阿里云SSL证书。

RDS支持开启SSL加密功能和将SSL证书安装到所需的应用服务中，以提升通信数据的安全性和完整性。

## 步骤一：开启SSL加密

1.  登录[RDS管理控制台](https://rdsnext.console.aliyun.com/rdsList/basic)。

2.  在**实例列表**页面，单击需要开启SSL加密的实例名称。

3.  在左侧导航栏，单击**数据安全性**。

4.  在**数据安全性**页面，单击**SSL**页签。

5.  在**SSL**页面，单击**开启SSL**，为该实例开启SSL加密。

    开启SSL加密后，需等待数分钟才能开启成功。

6.  下载证书。

    有关开启SSL加密服务的详细内容，请参见[设置SSL加密](/cn.zh-CN/RDS MySQL 数据库/数据安全/加密/设置SSL加密.md)。

    如果现有证书无法满足您的需求，可前往阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)购买新的证书。在SSL证书控制台购买的证书会自动同步到您的RDS实例中。


## 步骤二：配置证书

开通SSL加密服务后，请参考以下步骤在您的数据库应用或客户端中配置SSL证书。

MySQL Workbench配置SSL证书

1.  打开MySQL Workbench。

2.  选择**Database** \> **Manage Connections**。

3.  启用**Use SSL**，并导入SSL CA证书。

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7140359951/p4150.png)


Navicat配置SSL证书

1.  打开Navicat。

2.  在目标数据库上单击鼠标右键，选择**编辑连接**。

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7140359951/p52885.png)

3.  选择**SSL**页签，选择.pem格式CA证书的路径。参照下图进行设置。

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7140359951/p52887.png)

4.  单击**确定**。

    **说明：** 如果报`connection is being used`错误，是由于之前的会话未断开，请关闭Navicat重新打开。

5.  双击目标数据库测试能否正常连接。

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7140359951/p52889.png)


