# CancelCertificateForPackageRequest

调用CancelCertificateForPackageRequest吊销已签发的证书（取消对应的证书申请订单）。

只有当证书申请订单的状态为**已签发**时，您才可以调用本接口取消对应的证书申请订单，并吊销已签发的证书。

**说明：** 您可以调用[DescribeCertificateState](~~164111~~)查询证书申请订单的状态，如果返回数据中的**Type**参数取值为**certificate**，则表示证书已签发。

如果证书在签发之日起的30个自然日内被吊销，则已消耗的证书资源包次数将会返还给您；否则，已消耗的证书资源包次数不会返还。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=CancelCertificateForPackageRequest&type=RPC&version=2020-04-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CancelCertificateForPackageRequest|要执行的操作。取值：**CancelCertificateForPackageRequest**。 |
|OrderId|Long|是|123451222|要取消的证书申请订单的ID。

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
http(s)://[Endpoint]/?Action=CancelCertificateForPackageRequest
&OrderId=123451222
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<CancelCertificateForPackageRequestResponse>
	  <RequestId>082FAB35-6AB9-4FD5-8750-D36673548E76</RequestId>
</CancelCertificateForPackageRequestResponse>
```

`JSON`格式

```
{
    "RequestId": "082FAB35-6AB9-4FD5-8750-D36673548E76"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

