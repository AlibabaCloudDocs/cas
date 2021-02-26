# API概览

本文汇总了SSL证书服务提供的与证书资源包相关的API。

关于使用证书资源包API申请证书的完整流程介绍，请参见[使用API申请证书的流程]()。

|API|描述|
|---|--|
|[DescribePackageState](/cn.zh-CN/API参考（2020-04-07）/DescribePackageState.md)|查询证书资源包的使用概况，包含已购买证书资源包的次数、已提交证书申请的次数、成功签发证书的次数。|
|[CreateCertificateForPackageRequest]()|提交证书申请。**说明：** 本接口可用于申请所有规格的证书（包含DV、OV证书），且支持选择CSR生成方式。 |
|[CreateCertificateRequest](/cn.zh-CN/API参考（2020-04-07）/CreateCertificateRequest.md)|提交DV证书申请。调用本接口时，SSL证书服务将自动为您创建CSR文件。**说明：** 本接口仅用于申请DV证书，不支持用于申请OV证书。 |
|[CreateCertificateWithCsrRequest](/cn.zh-CN/API参考（2020-04-07）/CreateCertificateWithCsrRequest.md)|使用您手动制作的CSR文件提交DV证书申请。**说明：** 本接口仅用于申请DV证书，不支持用于申请OV证书。 |
|[DescribeCertificateState](/cn.zh-CN/API参考（2020-04-07）/DescribeCertificateState.md)|查询证书申请订单的状态，包含**待验证**、**审核中**、**审核失败**、**已签发**。|
|[CancelOrderRequest]()|撤回**待验证**、**审核中**的证书申请订单。订单撤回后，订单状态变更为**待申请**（该状态下已消耗的证书资源包次数不会返还）。 |
|[DeleteCertificateRequest](/cn.zh-CN/API参考（2020-04-07）/DeleteCertificateRequest.md)|删除**审核失败**、**待申请**的证书申请订单。订单删除后，已消耗的证书资源包次数将会返还给您。 |
|[CancelCertificateForPackageRequest]()|吊销**已签发**的证书（取消对应的申请订单）。在证书签发之日起的30个自然日内吊销证书，已消耗的证书资源包次数将会返还给您；否则，已消耗的证书资源包次数不会返还。 |
|[RenewCertificateOrderForPackageRequest]()|续费**已签发**的证书申请订单。|

