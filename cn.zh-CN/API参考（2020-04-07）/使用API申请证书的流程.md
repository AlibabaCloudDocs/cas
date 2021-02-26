# 使用API申请证书的流程

本文介绍了使用SSL证书服务的证书资源包API申请证书的完整流程，方便您在业务中调用相关接口。

|步骤|操作说明|操作结果|此时不想继续申请了该怎么办|
|--|----|----|-------------|
|1|调用[DescribePackageState](/cn.zh-CN/API参考（2020-04-07）/DescribePackageState.md)查询证书资源包的使用概况。|如果证书资源包的剩余次数无法满足您的需求，您需要先购买证书资源包。关于如何购买证书资源包，请参见[购买证书资源包](/cn.zh-CN/证书购买/购买证书资源包.md)。

|如果您已经购买了证书资源包但不想继续使用了，可以通过[SSL证书控制台](https://yundun.console.aliyun.com/?p=cas#/)的**证书资源包**页面申请退款。**说明：** 证书资源包购买后，在未使用的情况下，支持随时申请退款。 |
|2|调用[CreateCertificateForPackageRequest](/cn.zh-CN/API参考（2020-04-07）/CreateCertificateForPackageRequest.md)提交证书申请。**说明：** 调用[CreateCertificateRequest](/cn.zh-CN/API参考（2020-04-07）/CreateCertificateRequest.md)和[CreateCertificateWithCsrRequest](/cn.zh-CN/API参考（2020-04-07）/CreateCertificateWithCsrRequest.md)也可以提交证书申请，但只能用于申请DV证书。推荐您使用CreateCertificateForPackageRequest（可以申请所有规格的证书）。

|获得证书申请订单ID（**OrderId**），此时订单状态为**待验证**。|首先调用[CancelOrderRequest](/cn.zh-CN/API参考（2020-04-07）/CancelOrderRequest.md)撤回订单（订单撤回后，订单状态变更为**待申请**），然后调用[DeleteCertificateRequest](/cn.zh-CN/API参考（2020-04-07）/DeleteCertificateRequest.md)删除订单（订单删除后，已消耗的证书资源包次数将返还给您）。|
|3|完成域名所有权验证。您需要在提交证书申请后，先调用[DescribeCertificateState](/cn.zh-CN/API参考（2020-04-07）/DescribeCertificateState.md)获取完成域名验证所需要的信息，然后在域名的DNS管理平台（DNS验证方式）或者域名服务器（文件验证方式）手动完成验证。

|订单状态变更为**审核中**。|首先调用[CancelOrderRequest](/cn.zh-CN/API参考（2020-04-07）/CancelOrderRequest.md)撤回订单（订单撤回后，订单状态变更为**待申请**），然后调用[DeleteCertificateRequest](/cn.zh-CN/API参考（2020-04-07）/DeleteCertificateRequest.md)删除订单（订单删除后，已消耗的证书资源包次数将返还给您）。|
|4|等待CA中心审核您的证书申请（DV证书一般在2个小时内完成，OV证书一般在2~5个工作日内完成），然后调用[DescribeCertificateState](/cn.zh-CN/API参考（2020-04-07）/DescribeCertificateState.md)查询订单状态（审核结果）。|订单状态为**审核失败**。**说明：** 审核失败可能是因为您提交的证书申请信息不正确。

|首先调用[DeleteCertificateRequest](/cn.zh-CN/API参考（2020-04-07）/DeleteCertificateRequest.md)删除订单（订单删除后，已消耗的证书资源包次数将返还给您），然后调用[CreateCertificateForPackageRequest](/cn.zh-CN/API参考（2020-04-07）/CreateCertificateForPackageRequest.md)重新提交证书申请。|
|订单状态为**已签发**，表示审核成功，证书已经签发，您可以通过返回数据获得已签发的证书文件和私钥文件。**说明：** 证书文件需要安装到Web服务器，相关操作，请参见[SSL证书安装指南](/cn.zh-CN/证书安装/SSL证书安装指南.md)。私钥文件需要您妥善保管。

|调用[CancelCertificateForPackageRequest](/cn.zh-CN/API参考（2020-04-07）/CancelCertificateForPackageRequest.md)吊销已签发的证书。如果证书在签发之日起的30个自然日内被吊销，则已消耗的证书资源包次数将返还给您；否则，已消耗的证书资源包次数不会返还。 |

