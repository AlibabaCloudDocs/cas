---
keyword: [SSL证书, 快速https, 证书免安装, 证书免部署]
---

# 快速上手（免安装SSL证书实现HTTPS）

如果您不了解如何在Web服务器安装证书，希望通过简单的操作为网站实现HTTPS，推荐您使用网站代理HTTPS。网站代理HTTPS支持免安装SSL证书实现网站HTTPS，且支持证书续费免配置，方便您快速和便捷地应用SSL证书。

## 为什么选择证书免安装方案？

SSL证书的有效期只有1年，每年到期前都需要重新申请新证书，并在服务器上替换旧证书。虽然您可以购买2年期、3年期时长的证书服务，但这些方案仍需要每年在服务器上替换一次证书。

基于网站代理HTTPS的证书免安装方案，使您无需在服务器上配置证书，只需修改域名解析设置，即可实现网站HTTPS。证书免安装方案只用在首次使用时进行简单配置，后续每年只要完成续费购买，即可延长服务时长，无需每年重新申请和配置证书，大大降低了网站HTTPS的运维成本。

## 适用场景

本方案适合帮助轻量级网站业务快速实现HTTPS，使用本方案的网站需要满足以下条件：

-   网站服务器通过标准的HTTP 80端口、HTTPS 443端口提供Web服务。
-   网站的日常QPS不超过100。
-   网站域名已完成ICP备案。
-   您拥有修改网站域名解析设置（DNS）的权限。
-   网站未应用基于代理的安全防护、网站加速服务（例如，DDoS防护、Web应用防火墙、CDN等）。

关于网站代理HTTPS详细的注意事项，请参见[使用限制](/cn.zh-CN/网站代理HTTPS/使用限制.md)。

## 步骤1：购买网站代理HTTPS实例

首先，您需要在[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)的**网站代理HTTPS**页面单击**购买**，并在**购买**面板购买一个**域名规格**的网站代理HTTPS实例。

![网站代理HTTPS-购买](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0977371261/p276567.png)

在购买配置中，根据您要实现HTTPS的网站域名，选择**域名类型**：

-   **单域名**：表示仅为一个具体的单域名（例如，`www.example.com`、`example.com`）实现HTTPS。本文以单域名规格为例。
-   **通配符域名**：表示为一个通配符域名（例如，`*.example.com`）实现HTTPS。

    通配符域名可以匹配同级别的所有子域名，例如，`*.example.com`可以匹配`www.example.com`、`123.example.com`等。

    **说明：** `*.example.com`不可以匹配`www.123.example.com`，因为`www.123.example.com`和`*.example.com`的级别不同。


更多配置说明，请参见[购买网站代理HTTPS实例](/cn.zh-CN/网站代理HTTPS/实例管理/购买网站代理HTTPS实例.md)。

**说明：** 网站代理HTTPS实例默认包含10 QPS的网站QPS阈值，表示能够正常处理的网站QPS不超过10。如果您要接入网站代理HTTPS实例的网站QPS超过10，您必须在购买网站代理HTTPS实例后升级实例，提高实例的QPS阈值规格，否则可能导致接入实例的网站访问异常（例如，响应缓慢、无响应等）。关于升级实例的相关操作，请参见[升级实例规格](/cn.zh-CN/网站代理HTTPS/实例管理/升级实例规格.md)。

## 步骤2：添加域名

购买网站代理HTTPS实例后，您可以在**网站代理HTTPS**页面查看已购买的实例。这时，您需要单击实例**操作**列下的**添加域名**，将要实现HTTPS的网站域名添加进来。

![网站代理HTTPS-添加域名](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0977371261/p276568.png)

添加域名需要您完成以下配置：

-   **证书绑定域名**：填写您的网站域名。本文以`install-free.domain.com`为例。
-   **域名验证方式**：根据您填写的**证书绑定域名**，自动匹配对应的验证方式，无需手动设置。如果您填写的是通过阿里云注册的域名，自动匹配**自动DNS验证**；如果您填写的是通过第三方平台注册的域名，自动匹配**手工DNS验证**。
-   **联系人**：设置联系人信息，便于在证书申请过程中遇到问题时与您取得联系。
-   **所在地**：选择您所在地域。
-   **CSR生成方式**：选择**系统生成**。

![网站代理HTTPS-添加域名](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1977371261/p276569.png)

完成上述配置后，单击**下一步**，进入域名所有权验证环节。

域名所有权验证表示验证上一步添加的域名属于您。根据您添加的域名是否通过阿里云注册，验证方式不同，具体说明如下：

-   如果域名是通过阿里云注册的，直接单击**验证**，并在收到**域名验证成功**的提示后，单击**提交审核**。

    ![网站代理HTTPS-域名验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1977371261/p276570.png)

-   如果域名是通过第三方平台注册的，则需要按照页面提示，前往域名对应的解析服务系统，修改域名解析设置（添加一条TXT类型的解析记录）。修改解析设置后，回到**添加域名**页面，单击**验证**，并在收到**域名验证成功**的提示后，单击**提交审核**。

更多配置说明，请参见[申请证书](/cn.zh-CN/网站代理HTTPS/接入服务/添加域名.md)。

提交审核后，网站代理HTTPS实例的**证书状态**将更新为**准备中**。

![网站代理HTTPS-证书状态（准备中）](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1977371261/p276571.png)

耐心等待2分钟左右，**证书状态**将更新为**正常**，表示SSL证书已经成功签发。

## 步骤3：设置源站IP地址

证书状态正常后，您需要再次单击网站代理HTTPS实例**操作**列下的**添加域名**，进行回源配置。

![网站代理HTTPS-回源配置（添加域名）](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1977371261/p276572.png)

回源配置包括：

-   **源站地址**：选择**IPv4**并填写源站服务器的公网IP地址。最多支持填写3个IP地址，多个IP地址间使用半角逗号（,）分隔。

    **说明：** 请勿填写私网IP地址，否则会报错。

-   **强制HTTPS访问**：表示使客户端浏览器的所有HTTP请求都跳转成HTTPS请求，实现网站HTTPS。建议保持开启，无需修改。
-   **TLS/SSL卸载**：表示让阿里云SSL证书服务器使用HTTP协议与您的源站服务器通信，减轻源站的负载压力。建议保持开启，无需修改。

![网站代理HTTPS-回源配置](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1977371261/p276573.png)

更多配置说明，请参见[添加回源配置](/cn.zh-CN/网站代理HTTPS/接入服务/添加域名.md)。

完成回源配置后，网站代理HTTPS实例的**CNAME**列下会生成一个CNAME值，且**接入状态**会更新为**异常**。

![网站代理HTTPS-接入状态异常](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1977371261/p276574.png)

您可以单击操作列下的**状态检测**，查看网站接入状态。返回结果如下图所示，表示您需要前往域名的解析服务系统，按照状态检测中的提示，添加指定的CNAME解析记录。

![网站代理HTTPS-状态检测](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1977371261/p276575.png)

## 步骤4：修改域名解析设置

**说明：** 以下操作描述以域名通过阿里云注册为例。如果您的域名是通过第三方平台注册的，请前往域名对应的解析服务系统，修改域名解析设置。

1.  登录[云解析DNS控制台](https://dns.console.aliyun.com/#/dns/domainList)。

    您也可以在SSL证书服务控制台，通过顶部菜单栏的搜索框，搜索**云解析**，并单击**云解析DNS**，前往云解析DNS控制台。

    ![搜索云解析](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1977371261/p276576.png)

2.  在**域名解析**页面，定位到您的域名，单击**操作**列下的**解析设置**。

    ![云解析-解析设置](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1977371261/p276577.png)

3.  在**解析设置**列表，通过**主机记录**（本文以`install-free`为例）定位到要操作的解析记录，执行以下操作：

    1.  将**TXT**类型的解析记录删除。

        该解析记录是[步骤2：添加域名](#section_2uh_w4f_8fz)中为完成域名所有权验证自动生成的记录值，此时证书已经签发，该解析记录已无效。

    2.  单击**A**类型解析记录**操作**列下的**修改**。

        如果当前主机记录没有对应的A类型解析记录，您可以单击列表上方的**添加记录**。

    ![云解析-解析设置修改](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1977371261/p276578.png)

4.  在**修改记录**（或者**添加记录**）对话框，按照[步骤3：设置源站IP地址](#section_svx_e6q_i1a)中**状态检测**的提示，设置**CNAME**类型解析记录，并单击**确认**。

    ![云解析-修改记录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1977371261/p276579.png)

    解析记录设置完成后，您可以在**解析设置**列表中查看CNAM解析记录的状态。此时，CNAME解析记录的**状态**为**正常**，表示该解析记录已生效。

    ![云解析-状态正常](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1977371261/p276580.png)


## 步骤5：验证HTTPS访问

完成解析设置后，回到**网站代理HTTPS**页面，刷新页面并查看域名的**接入状态**。域名的**接入状态**将更新为**正常**。

**说明：** 如果您的源站服务器上安装了安全狗、云锁等安全软件，您必须在源站安全软件上放行网站代理HTTPS的回源IP地址，否则网站代理HTTPS的回源流量可能会被源站安全软件拦截，导致网站响应异常。更多信息，请参见[放行回源IP地址段](/cn.zh-CN/网站代理HTTPS/接入服务/放行回源IP地址段.md)。

![网站代理HTTPS-接入状态正常](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1977371261/p276581.png)

这时，您可以使用浏览器访问域名，验证是否已成功实现HTTPS。返回结果如下。

![连接安全](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1977371261/p276582.png)

浏览器的地址栏出现了![锁状图标](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5742471261/p276584.png)图标，表示客户端与服务端已成功建立HTTPS安全连接。单击![锁状图标](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5742471261/p276584.png)标识，可以查看到证书的状态为**有效**。

## 后续步骤

完成首次配置后，后续您只需关注网站代理HTTPS实例的**到期时间**。在距离网站代理HTTPS实例到期前的30个自然日，您将会收到服务续费提醒。这时，您只需在**网站代理HTTPS**页面执行**续费购买**操作，即可延长证书服务时长，无需其他任何配置。

**说明：** **续费购买**操作仅在网站代理HTTPS实例到期前的30个自然日内开放，其余时间不支持操作。

![续费购买](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2977371261/p276583.png)

