# RenewCertificateOrderForPackageRequest

调用RenewCertificateOrderForPackageRequest为已签发的证书申请订单续费。

只有当证书申请订单的状态为已签发且已签发证书处于有效期内时，您才可以调用本接口为对应的证书申请订单续费，将已签发证书的有效期延长一年。

**说明：** 您可以调用[DescribeCertificateState](~~164111~~)查询证书申请订单的状态，如果返回数据中的**Type**参数取值为**certificate**，则表示证书已签发。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=RenewCertificateOrderForPackageRequest&type=RPC&version=2020-04-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RenewCertificateOrderForPackageRequest|要执行的操作。取值：**RenewCertificateOrderForPackageRequest**。 |
|OrderId|Long|是|123451222|要续费的证书申请订单的ID。

 **说明：** 您在调用[CreateCertificateForPackageRequest](~~204087~~)、[CreateCertificateRequest](~~164105~~)、[CreateCertificateWithCsrRequest](~~178732~~)接口提交证书申请后，可以从请求返回数据中获取对应的证书申请订单ID（即**OrderId**）。 |
|Csr|String|否|-----BEGIN CERTIFICATE REQUEST----- MIIC1TCCAb0CAQAwgY8xCzAJBgNVBAYTAkNOMRIwEAYDVQQIDAlHdWFuZ3pob3Ux ETAPBgNVBAcMCFNoZW56aGVuMQ8wDQYDVQQKDAZDaGFjdW8xEDAOBgNVBAsMB0lU IERlcHQxFzAVBgNVBAMMDnd3dy5jaGFjdW8ubmV0MR0wGwYJKoZIhvcNAQkBFg44 MjkyNjY5QHFxLmNvbTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALo7 atRvQf9tKo1NJ/MQqzHvIjHNhU+0MMerDq+tRlJ+a7Ro1r6IWNF5MB0Z\*\*\*\*\*\* -----END CERTIFICATE REQUEST-----|您使用OpenSSL或Keytool工具为域名手动生成的CSR文件的内容。CSR文件的密钥类型必须是RSA、ECC算法，且RSA算法的密钥长度必须大于等于2048。关于CSR文件的制作方法，请参见[如何制作CSR文件](~~42218~~)。

 如果不设置该参数，表示使用待续费证书申请订单中的域名，由SSL证书服务自动为您生成新的CSR。

 CSR（Certificate Signing Request）是证书签名请求文件，包含了您的服务器信息和公司信息。申请证书时需要将您证书的CSR文件提交给CA认证中心审核，CA中心对CSR文件进行根证书私钥签名后，会生成证书公钥文件（即签发给您的SSL证书）。

 **说明：** CSR中的**CN**字段表示证书绑定的域名。 |

调用API时，除了本文中该API的请求参数，还需加入阿里云API公共请求参数。公共请求参数的详细介绍，请参见[公共参数](~~164108~~)。

调用API的请求格式，请参见本文**示例**中的请求示例。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|082FAB35-6AB9-4FD5-8750-D36673548E76|本次请求的ID。 |
|OrderId|Long|323451222|本次证书申请（续费）订单的ID。

 **说明：** 后续您可以使用该ID查询证书申请订单的状态，具体操作，请参见[DescribeCertificateState](~~164111~~)。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=RenewCertificateOrderForPackageRequest
&OrderId=123451222
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RenewCertificateOrderForPackageRequestResponse>
	  <RequestId>082FAB35-6AB9-4FD5-8750-D36673548E76</RequestId>
	  <OrderId>323451222</OrderId>
</RenewCertificateOrderForPackageRequestResponse>
```

`JSON`格式

```
{
    "RequestId": "082FAB35-6AB9-4FD5-8750-D36673548E76",
    "OrderId": "323451222"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

