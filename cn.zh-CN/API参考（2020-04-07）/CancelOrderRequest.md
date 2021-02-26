# CancelOrderRequest

调用CancelOrderRequest撤回待验证、审核中的证书申请订单。

只有在以下场景下，您才可以调用本接口撤回对应的证书申请订单：

-   订单处于**待验证**状态：您已经提交了证书申请，但是还没有完成域名所有权验证。
-   订单处于**审核中**状态：您已经提交了证书申请且完成了域名所有权验证，但CA中心还没有审核完成。

证书申请订单被撤回后，状态将变更为**待申请**。此时，您只有调用[DeleteCertificateRequest](~~164109~~)删除证书申请订单后，已消耗的资源包次数才会返还给您。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=CancelOrderRequest&type=RPC&version=2020-04-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CancelOrderRequest|要执行的操作。取值：**CancelOrderRequest**。 |
|OrderId|Long|是|123451222|要撤回的证书申请订单的ID。

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
http(s)://[Endpoint]/?Action=CancelOrderRequest
&OrderId=123451222
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<CancelOrderRequestResponse>
        <RequestId>082FAB35-6AB9-4FD5-8750-D36673548E76</RequestId>
</CancelOrderRequestResponse>
```

`JSON`格式

```
{
    "RequestId": "082FAB35-6AB9-4FD5-8750-D36673548E76"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

