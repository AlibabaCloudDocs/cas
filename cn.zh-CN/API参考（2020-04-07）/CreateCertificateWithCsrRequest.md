# CreateCertificateWithCsrRequest

调用CreateCertificateWithCsrRequest购买、申请和签发自带CSR文件的DV证书。针对批量购买证书的场景，证书扩展服务可通过调用该API一步完成DV证书的购买和申请。

**说明：** 您购买了证书扩展服务后，才可以使用该API。具体请参见[证书扩展服务](~~165099~~)。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=CreateCertificateWithCsrRequest&type=RPC&version=2020-04-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateCertificateWithCsrRequest|要执行的操作。取值：

 **CreateCertificateWithCsrRequest**。 |
|Csr|String|是|-----BEGIN CERTIFICATE REQUEST----- MIIC1TCCAb0CAQAwgY8xCzAJBgNVBAYTAkNOMRIwEAYDVQQIDAlHdWFuZ3pob3Ux ETAPBgNVBAcMCFNoZW56aGVuMQ8wDQYDVQQKDAZDaGFjdW8xEDAOBgNVBAsMB0lU IERlcHQxFzAVBgNVBAMMDnd3dy5jaGFjdW8ubmV0MR0wGwYJKoZIhvcNAQkBFg44 MjkyNjY5QHFxLmNvbTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALo7 atRvQf9tKo1NJ/MQqzHvIjHNhU+0MMerDq+tRlJ+a7Ro1r6IWNF5MB0Z\*\*\*\*\*\* -----END CERTIFICATE REQUEST-----|CSR（Certificate Signing Request）是证书签名请求文件，包含了您的服务器信息和公司信息。申请证书时需要将您证书的CSR文件提交给CA认证中心审核，CA中心对CSR文件进行根证书私钥签名后会生成证书公钥文件（即签发给您的SSL证书）。

 **说明：** 该接口的CSR文件由您自己使用OpenSSL或Keytool工具手动生成。 |
|Email|String|是|example@aliyun.com|申请人邮箱。 |
|Phone|String|是|1381111\*\*\*\*|申请人手机号。 |
|Username|String|是|keller|申请人姓名。 |
|ValidateType|String|是|DNS|域名所有权验证方式。取值：

 -   **DNS**：手动DNS验证。如果您需要保护的域名是非阿里云域名，您需要到该域名的管理平台中为该域名添加一条TXT类型的DNS记录。例如：如果您购买的是A公司的域名，您需要到A公司的域名管理平台添加DNS记录。
-   **FILE**：文件验证，通过在您域名服务器上创建指定文件来验证该域名的所有权。 |
|ProductCode|String|否|symantec-free-1-free|证书品牌类型。取值：

 -   **symantec-free-1-free**：免费单域名证书
-   **symantec-dv-1-starter**：Digicert DV通配符证书
-   **geotrust-dv-w-starter**：Geotrust DV通配符证书
-   **geotrust-dv-1-starter**：Geotrust DV单域名证书
-   **globalsign-dv-1-personal**：Globalsign DV单域名证书
-   **globalsign-dv-w-advanced**：Globalsign DV通配符证书 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|OrderId|Long|98987582437920968|订单证书ID。 |
|RequestId|String|CBF1E9B7-D6A0-4E9E-AD3E-2B47E6C2837D|阿里云为该请求生成的唯一标识符。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateCertificateWithCsrRequest
&Csr=-----BEGIN CERTIFICATE REQUEST----- MIIC1TCCAb0CAQAwgY8xCzAJBgNVBAYTAkNOMRIwEAYDVQQIDAlHdWFuZ3pob3Ux ETAPBgNVBAcMCFNoZW56aGVuMQ8wDQYDVQQKDAZDaGFjdW8xEDAOBgNVBAsMB0lU IERlcHQxFzAVBgNVBAMMDnd3dy5jaGFjdW8ubmV0MR0wGwYJKoZIhvcNAQkBFg44 MjkyNjY5QHFxLmNvbTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALo7 atRvQf9tKo1NJ/MQqzHvIjHNhU+0MMerDq+tRlJ+a7Ro1r6IWNF5MB0Z****** -----END CERTIFICATE REQUEST-----
&Email=example@aliyun.com
&Phone=1381111****
&Username=keller
&ValidateType=DNS
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateCertificateWithCsrRequestResponse>
      <RequestId>CBF1E9B7-D6A0-4E9E-AD3E-2B47E6C2837D</RequestId>
      <OrderId>98987582437920968</OrderId>
</CreateCertificateWithCsrRequestResponse>
```

`JSON` 格式

```
{
    "RequestId":"CBF1E9B7-D6A0-4E9E-AD3E-2B47E6C2837D",
    "OrderId":"98987582437920968"
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

|套餐中不可用的证书数量。 |
|403

|CreateCertificateRequestFailed

|创建请求失败。 |
|404

|NotFoundOrder

|没有找到证书订单。 |
|403

|OrderStateError

|证书订单状态错误。 |
|403

|DeleteFail

|删除证书订单失败。 |
|500

|Error

|发生错误。 |

