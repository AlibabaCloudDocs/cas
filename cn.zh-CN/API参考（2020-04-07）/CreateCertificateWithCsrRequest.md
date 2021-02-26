# CreateCertificateWithCsrRequest

调用CreateCertificateWithCsrRequest使用您手动制作的CSR文件提交DV证书申请。

**说明：** 本接口仅用于申请DV证书，不支持用于申请OV证书。推荐您使用[CreateCertificateForPackageRequest](~~204087~~)接口提交证书申请（可用于申请所有规格的证书，且支持选择CSR生成方式）。

调用本接口提交证书申请并成功签发证书后，将会消耗您已购买的对应规格的证书资源包的个数。您在发起请求时，可以通过**ProductCode**参数指定要申请的证书规格。

关于使用证书资源包API申请证书的完整流程，请参见[使用API申请证书的流程](~~204741~~)。

发起请求前，请确保您已购买对应规格的证书资源包。关于如何购买证书资源包，请参见[购买证书资源包](~~188316~~)。您可以调用[DescribePackageState](~~164110~~)查询指定规格的证书资源包的使用概况，包含已购买该规格证书资源包的总数、已提交证书申请的次数、成功签发证书的次数。

调用本接口提交证书申请后，您还需要调用[DescribeCertificateState](~~164111~~)接口，获取完成域名验证所需要的信息，并在域名的DNS管理平台（DNS验证方式）或者域名服务器（文件验证方式）手动完成验证，然后证书申请订单才会进入CA中心审核环节。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=CreateCertificateWithCsrRequest&type=RPC&version=2020-04-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateCertificateWithCsrRequest|要执行的操作。取值：**CreateCertificateWithCsrRequest**。 |
|Csr|String|是|-----BEGIN CERTIFICATE REQUEST----- MIIC1TCCAb0CAQAwgY8xCzAJBgNVBAYTAkNOMRIwEAYDVQQIDAlHdWFuZ3pob3Ux ETAPBgNVBAcMCFNoZW56aGVuMQ8wDQYDVQQKDAZDaGFjdW8xEDAOBgNVBAsMB0lU IERlcHQxFzAVBgNVBAMMDnd3dy5jaGFjdW8ubmV0MR0wGwYJKoZIhvcNAQkBFg44 MjkyNjY5QHFxLmNvbTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALo7 atRvQf9tKo1NJ/MQqzHvIjHNhU+0MMerDq+tRlJ+a7Ro1r6IWNF5MB0Z\*\*\*\*\*\* -----END CERTIFICATE REQUEST-----|您使用OpenSSL或Keytool工具为域名手动生成的CSR文件的内容。CSR文件的密钥类型必须是RSA、ECC算法，且RSA算法的密钥长度必须大于等于2048。关于CSR文件的制作方法，请参见[如何制作CSR文件](~~42218~~)。

 CSR（Certificate Signing Request）是证书签名请求文件，包含了您的服务器信息和公司信息。申请证书时需要将您证书的CSR文件提交给CA认证中心审核，CA中心对CSR文件进行根证书私钥签名后，会生成证书公钥文件（即签发给您的SSL证书）。

 **说明：** CSR中的**CN**字段表示证书绑定的域名。 |
|Username|String|是|keller|申请联系人的姓名。 |
|Email|String|是|example@aliyun.com|申请联系人的邮箱地址。 |
|Phone|String|是|1381111\*\*\*\*|申请联系人的手机号码。 |
|ValidateType|String|是|DNS|域名所有权的验证方式。取值：

 -   **DNS**：DNS验证。通过在域名的DNS管理平台为域名添加一条TXT类型的DNS记录，验证域名的所有权。您需要域名解析的管理权限，才可以完成验证。
-   **FILE**：文件验证。通过在域名服务器上创建指定的文件，验证域名的所有权。您需要域名服务器的管理员权限，才可以完成验证。

 关于两种验证方式的更多信息，请参见[如何配置域名授权验证？](~~48016~~)。 |
|ProductCode|String|否|symantec-free-1-free|要申请的证书规格。取值：

 -   **symantec-free-1-free**（默认）：表示免费单域名证书。
-   **symantec-dv-1-starter**：表示DigiCert DV单域名证书。
-   **geotrust-dv-1-starter**：表示GeoTrust DV单域名证书。
-   **geotrust-dv-w-starter**：表示GeoTrust DV通配符域名证书。
-   **globalsign-dv-1-personal**：表示GlobalSign DV单域名证书。
-   **globalsign-dv-w-advanced**：表示GlobalSign DV通配符域名证书。 |

调用API时，除了本文中该API的请求参数，还需加入阿里云API公共请求参数。公共请求参数的详细介绍，请参见[公共参数](~~164108~~)。

调用API的请求格式，请参见本文**示例**中的请求示例。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|OrderId|Long|98987582437920968|本次证书申请订单的ID。

 **说明：** 后续您可以使用该ID查询证书的申请状态，具体操作，请参见[DescribeCertificateState](~~164111~~)。 |
|RequestId|String|CBF1E9B7-D6A0-4E9E-AD3E-2B47E6C2837D|本次请求的ID。 |

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

`XML`格式

```
<CreateCertificateWithCsrRequestResponse>
      <RequestId>CBF1E9B7-D6A0-4E9E-AD3E-2B47E6C2837D</RequestId>
      <OrderId>98987582437920968</OrderId>
</CreateCertificateWithCsrRequestResponse>
```

`JSON`格式

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

