# CreateCertificateForPackageRequest

调用CreateCertificateForPackageRequest提交证书申请。

调用本接口提交证书申请并成功签发证书后，将会消耗您已购买的对应规格的证书资源包的个数。您在发起请求时，可以通过**ProductCode**参数指定要申请的证书规格。

关于使用证书资源包API申请证书的完整流程，请参见[使用API申请证书的流程](~~204741~~)。

发起请求前，请确保您已购买对应规格的证书资源包。关于如何购买证书资源包，请参见[购买证书资源包](~~188316~~)。您可以调用[DescribePackageState](~~164110~~)查询指定规格的证书资源包的使用概况，包含已购买该规格证书资源包的总数、已提交证书申请的次数、成功签发证书的次数。

调用本接口提交证书申请后，您还需要调用[DescribeCertificateState](~~164111~~)接口，获取完成域名验证所需要的信息，并在域名的DNS管理平台（DNS验证方式）或者域名服务器（文件验证方式）手动完成验证，然后证书申请订单才会进入CA中心审核环节。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=CreateCertificateForPackageRequest&type=RPC&version=2020-04-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateCertificateForPackageRequest|要执行的操作。取值：**CreateCertificateForPackageRequest**。 |
|ProductCode|String|否|symantec-free-1-free|要申请的证书规格。取值：

 -   **symantec-free-1-free**（默认）：表示免费单域名证书。
-   **symantec-dv-1-starter**：表示DigiCert DV单域名证书。
-   **symantec-ov-1-personal**：表示DigiCert OV单域名证书。
-   **symantec-ov-w-personal**：表示DigiCert OV通配符域名证书。
-   **geotrust-dv-1-starter**：表示GeoTrust DV单域名证书。
-   **geotrust-dv-w-starter**：表示GeoTrust DV通配符域名证书。
-   **geotrust-ov-1-personal**：表示GeoTrust OV单域名证书。
-   **geotrust-ov-w-personal**：表示GeoTrust OV通配符域名证书。
-   **globalsign-dv-1-personal**：表示GlobalSign DV单域名证书。
-   **globalsign-dv-w-advanced**：表示GlobalSign DV通配符域名证书。
-   **globalsign-ov-1-personal**：表示GlobalSign OV单域名证书。
-   **globalsign-ov-w-advanced**：表示GlobalSign OV通配符域名证书。
-   **cfca-ov-1-personal**：表示CFCA OV单域名证书。
-   **cfca-ev-w-advanced**：表示CFCA OV通配符域名证书。 |
|Domain|String|否|www.aliyun.com|证书要绑定的域名。具体要求如下：

 -   支持设置单域名（例如，`www.aliyun.com`）或者通配符域名（例如，`*.aliyun.com`）。
-   支持设置多个域名。多个域名间使用英文逗号（,）分隔。最多可以设置5个域名。
-   如果设置多个域名，则多个域名只能全部是单域名或者通配符域名，不允许同时包含单域名和通配符域名。

 **说明：** 该参数与**Csr**参数不允许同时为空。如果您同时设置了该参数和**Csr**参数，则取**Csr**中的**CN**字段值作为证书绑定的域名。 |
|Csr|String|否|-----BEGIN CERTIFICATE REQUEST----- MIIC1TCCAb0CAQAwgY8xCzAJBgNVBAYTAkNOMRIwEAYDVQQIDAlHdWFuZ3pob3Ux ETAPBgNVBAcMCFNoZW56aGVuMQ8wDQYDVQQKDAZDaGFjdW8xEDAOBgNVBAsMB0lU IERlcHQxFzAVBgNVBAMMDnd3dy5jaGFjdW8ubmV0MR0wGwYJKoZIhvcNAQkBFg44 MjkyNjY5QHFxLmNvbTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALo7 atRvQf9tKo1NJ/MQqzHvIjHNhU+0MMerDq+tRlJ+a7Ro1r6IWNF5MB0Z\*\*\*\*\*\* -----END CERTIFICATE REQUEST-----|您使用OpenSSL或Keytool工具为域名手动生成的CSR文件的内容。CSR文件的密钥类型必须是RSA、ECC算法，且RSA算法的密钥长度必须大于等于2048。关于CSR文件的制作方法，请参见[如何制作CSR文件](~~42218~~)。如果不设置该参数，表示由SSL证书服务自动为您创建CSR。

 CSR（Certificate Signing Request）是证书签名请求文件，包含了您的服务器信息和公司信息。申请证书时需要将您证书的CSR文件提交给CA认证中心审核，CA中心对CSR文件进行根证书私钥签名后，会生成证书公钥文件（即签发给您的SSL证书）。

 **说明：** CSR中的**CN**字段表示证书绑定的域名。如果您设置了该参数，则无需设置**Domain**参数。 |
|ValidateType|String|否|DNS|域名所有权的验证方式。取值：

 -   **DNS**：DNS验证。通过在域名的DNS管理平台为域名添加一条TXT类型的DNS记录，验证域名的所有权。您需要域名解析的管理权限，才可以完成验证。
-   **FILE**：文件验证。通过在域名服务器上创建指定的文件，验证域名的所有权。您需要域名服务器的管理员权限，才可以完成验证。

 关于两种验证方式的更多信息，请参见[如何配置域名授权验证？](~~48016~~)。 |
|Username|String|否|Tom Zhang|申请联系人的姓名。

 如果不设置该参数，表示从**信息管理**模块中选择使用最新添加的一条联系人信息。关于在**信息管理**模块中添加联系人的具体操作，请参见[管理联系人](~~198262~~)。 |
|Email|String|否|tom.zhang@example.com|申请联系人的邮箱地址。CA中心收到您的证书申请后，将向该邮箱发送一封证书申请验证邮件。您需要登录该邮箱，查收相关邮件，并按照邮件提示完成验证。

 如果不设置该参数，表示从**信息管理**模块中选择使用最新添加的一条联系人信息。关于在**信息管理**模块中添加联系人的具体操作，请参见[管理联系人](~~198262~~)。 |
|Phone|String|否|13000000000|申请联系人的手机号码。后续CA中心工作人员可能会通过该电话联系您，验证您的证书申请信息。

 如果不设置该参数，表示从**信息管理**模块中选择使用最新添加的一条联系人信息。关于在**信息管理**模块中添加联系人的具体操作，请参见[管理联系人](~~198262~~)。 |
|CompanyName|String|否|阿里云|证书申请公司的名称。

 **说明：** 该参数仅适用于申请OV证书。申请OV证书时，您必须先在[SSL证书控制台](https://yundun.console.aliyun.com/?p=cas#/)的**信息管理**模块添加公司信息，具体操作，请参见[管理公司信息](~~198289~~)。申请DV证书时，无需添加公司信息。

 申请OV证书时，如果您在此处设置了公司名称，则表示使用**信息管理**模块中对应的公司信息；如果您没有设置该参数，则表示从**信息管理**模块中选择使用最新添加的一条公司信息。 |

调用API时，除了本文中该API的请求参数，还需加入阿里云API公共请求参数。公共请求参数的详细介绍，请参见[公共参数](~~164108~~)。

调用API的请求格式，请参见本文**示例**中的请求示例。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|98C8BF38-2984-4E55-90DD-3DEB8DE04384|本次请求的ID。 |
|OrderId|Long|98987582437920968|本次证书申请订单的ID。

 **说明：** 后续您可以使用该ID查询证书申请订单的状态，具体操作，请参见[DescribeCertificateState](~~164111~~)。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateCertificateForPackageRequest
&ProductCode=symantec-free-1-free
&Domain=www.aliyun.com
&ValidateType=DNS
&Username=Tom Zhang
&Email=tom.zhang@example.com
&Phone=13000000000
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<CreateCertificateForPackageRequestResponse>
	  <RequestId>98C8BF38-2984-4E55-90DD-3DEB8DE04384</RequestId>
      <OrderId>98987582437920968</OrderId>
</CreateCertificateForPackageRequestResponse>
```

`JSON`格式

```
{
    "RequestId": "98C8BF38-2984-4E55-90DD-3DEB8DE04384",
    "OrderId": 98987582437920968
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

