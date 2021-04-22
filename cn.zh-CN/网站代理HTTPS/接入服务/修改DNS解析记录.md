# 修改DNS解析记录

通过网站代理HTTPS实例添加域名后，您必须手动将域名的DNS解析记录修改为SSL证书服务的CNAME地址，才可以正式为网站接入HTTPS代理，实现所有网站请求经过强制HTTPS跳转后再转发到源站服务器。本文以阿里云云解析DNS为例，介绍如何修改DNS解析记录。

-   已通过网站代理HTTPS实例添加域名。更多信息，请参见[添加域名](/cn.zh-CN/网站代理HTTPS/接入服务/添加域名.md)。
-   已获取域名对应的SSL证书服务CNAME地址。

    成功添加域名到网站代理HTTPS实例后，您可以在[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)的**网站代理HTTPS**页面，查询域名对应的SSL证书服务**CNAME**地址。

    ![添加回源配置](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2366160161/p224010.png)


## 操作步骤

修改域名DNS解析需要通过域名的DNS服务商的系统进行操作。如果您的域名解析托管在阿里云云解析DNS，可以参照以下步骤进行操作；如果域名解析没有托管在云解析DNS，请前往DNS服务商的系统进行操作。

1.  登录[云解析DNS控制台](https://dns.console.aliyun.com/)。

2.  在**域名解析**页面，定位到要操作的域名，单击**操作**列下的**解析设置**。

3.  在**解析设置**页面，定位到要操作的**主机记录**（**记录类型**为**A**或**CNAME**），单击**操作**列下的**修改**。

4.  在**修改记录**面板，选择**记录类型**为**CNAME**，并在**记录值**中填写域名对应的SSL证书服务CNAME地址。

    ![修改记录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2366160161/p224153.png)

    成功添加域名到网站代理HTTPS实例后，您可以在[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)的**网站代理HTTPS**页面，查询域名对应的SSL证书服务**CNAME**地址。

    ![添加回源配置](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2366160161/p224010.png)

    **说明：** 不同DNS解析记录类型间存在冲突。例如，对于同一个主机记录，CNAME记录与A记录、MX记录、TXT记录等其他记录互相冲突。在无法直接修改记录类型或提示记录冲突的情况下，您可以先删除存在冲突的其他记录（例如，TXT记录、A记录），再添加一条新的CNAME记录。更多信息，请参见[解析记录冲突规则](https://help.aliyun.com/document_detail/39787.html)。

5.  单击**确认**。

    成功修改DNS解析记录后，解析记录的**状态**显示为**正常**。这时，您可以在本地计算机上，使用ping命令（`ping yourdomain`）验证修改后的解析记录是否已经生效。

    ![ping](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2366160161/p224360.png)

    如果ping命令的执行请求被解析到域名对应的SSL证书服务CNAME地址，则表示解析记录已经生效。

    **说明：** 由于DNS解析记录生效需要一定时间，如果验证失败，您可以等待10分钟后重新检查。

6.  验证域名接入状态。

    修改后的解析记录生效后，您可以在[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)的**网站代理HTTPS**页面，查询域名的**接入状态**。

    ![接入状态正常](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2366160161/p224364.png)

    此时，域名的**接入状态**将会更新为**正常**，表示网站域名已经成功接入网站代理HTTPS服务。网站的Web请求将会被转发到网站代理HTTPS实例，经过强制HTTPS跳转后，再转发到源站服务器。


## 相关操作（流量切回源站）

后续如果您不再需要使用HTTPS代理，您可以参照本文介绍，手动将域名的DNS解析记录从SSL证书服务的CNAME地址修改为源站地址。这样，网站的Web请求流量将直接到达源站服务器，不会经过HTTPS代理。

