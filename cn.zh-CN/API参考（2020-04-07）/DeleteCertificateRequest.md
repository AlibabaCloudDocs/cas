# DeleteCertificateRequest

调用DeleteCertificateRequest删除审核失败、待申请的证书申请订单。证书申请订单被删除后，已消耗的资源包次数将会返还给您。

只有在以下场景下，您才可以调用本接口删除对应的证书申请订单：

-   订单处于**审核失败**状态：您已经调用[DescribeCertificateState](~~164111~~)查询了证书申请订单的状态，发现订单状态为审核失败（返回数据中的**Type**取值为**verify\_fail**）。
-   订单处于**待申请**状态：您已经调用[CancelOrderRequest](~~204298~~)撤回了待验证、审核中的证书申请订单。被撤回的证书申请订单的状态变更为**待申请**。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=DeleteCertificateRequest&type=RPC&version=2020-04-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteCertificateRequest|要执行的操作。取值：**DeleteCertificateRequest**。 |
|OrderId|Long|是|123451222|要删除的证书申请订单的ID。

 **说明：** 您在调用[CreateCertificateForPackageRequest](~~204087~~)、[CreateCertificateRequest](~~164105~~)、[CreateCertificateWithCsrRequest](~~178732~~)接口提交证书申请后，可以从请求返回数据中获取对应的证书申请订单ID（即**OrderId**）。 |

调用API时，除了本文中该API的请求参数，还需加入阿里云API公共请求参数。公共请求参数的详细介绍，请参见[公共参数](~~164108~~)。

调用API的请求格式，请参见本文**示例**中的请求示例。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|082FAB35-6AB9-4FD5-8750-D36673548E76|本次请求的ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteCertificateRequest
&OrderId=123451222
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DeleteCertificateRequestResponse>
    <RequestId>082FAB35-6AB9-4FD5-8750-D36673548E76</RequestId>
</DeleteCertificateRequestResponse>
```

`JSON`格式

```
{
    "RequestId": "082FAB35-6AB9-4FD5-8750-D36673548E76"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

|HttpCode

|错误码

|描述 |
|----------|-----|----|
|404

|NotFoundPackage

|没有购买套餐包。 |
|404

|NotRemainCount

|套餐中不可用的证书的数量。 |
|403

|CreateCertificateRequestFailed

|创建请求失败。 |
|404

|NotFoundOrder

|没有找到订单 。 |
|403

|OrderStateError

|订单状态错误。 |
|403

|DeleteFail

|删除失败 。 |
|500

|Error

|发生错误 。 |

