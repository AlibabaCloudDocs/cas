# 购买网站代理HTTPS实例

阿里云SSL证书服务提供网站代理HTTPS服务，帮助您为网站域名下所有页面一键配置HTTPS访问。您必须购买一个网站代理HTTPS实例，才可以开通网站代理HTTPS服务。

网站代理HTTPS服务需要单独购买。关于网站代理HTTPS实例的计费信息，请参见[一键式HTTPS](/cn.zh-CN/计量计费/计费方式.md)。

关于网站代理HTTPS功能的详细介绍，请参见[服务介绍](/cn.zh-CN/网站代理HTTPS/概述.md)。

## 操作步骤

1.  登录[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)。

2.  在左侧导航栏，单击**网站代理HTTPS**。

3.  在**网站代理HTTPS**页签下，单击**购买**。

4.  在**购买**面板，完成以下购买配置，并单击**立即购买**。

    |参数|说明|
    |--|--|
    |**商品规格**|默认已选择**域名规格**。不支持修改。|
    |**域名类型**|选择要代理的域名的类型。可选项：    -   **单域名**：表示一个具体的域名。例如，aliyun.com、www.aliyun.com。适用于只接入网站的一个域名（例如，www.yourdoman.com）的场景。
    -   **通配符**：表示一个通配符域名。例如，\*.aliyun.com（包含aliyun.com、www.aliyun.com、abc.aliyun.com等）、\*.abc.aliyun.com（包含abc.aliyun.com、www.abc.aliyun.com、a.abc.aliyun.com等）。适用于接入网站域名及其多个子域名（例如，www.yourdomain.com、abc.yourdomain.com）的场景。 |
    |**QPS阈值/日**|默认已选择**10QPS**。不支持修改。|
    |**购买时长**|默认已选择**1年**。不支持修改。|

5.  确认订单并完成支付。

    成功购买网站代理HTTPS实例后，您可以在**网站代理HTTPS**页签下查看新购买的实例。

    ![网站HTTPS代理实例](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7902171161/p223923.png)

    新购买实例的**证书状态**为**未申请**，您还需要为实例申请证书，才能开启代理服务。更多信息，请参见[添加域名](/cn.zh-CN/网站代理HTTPS/添加域名.md)。


