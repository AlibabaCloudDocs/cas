# DescribeCertificateState

调用DescribeCertificateState查询指定的证书申请订单的状态。

如果您在提交证书申请后还没有完成域名所有权验证，则调用本接口可以获取完成域名验证所需要的信息；您可以根据返回的域名验证信息，在域名的DNS管理平台（DNS验证方式）或者域名服务器（文件验证方式）上，完成域名验证。

只有当您完成域名验证后，证书申请才会进入CA中心审核环节。CA中心审核通过您的证书申请后，将会为您签发证书。如果证书已经签发，调用本接口可以获取已签发的证书文件和私钥内容。

关于使用证书资源包API申请证书的完整流程，请参见[使用API申请证书的流程](~~204741~~)。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=DescribeCertificateState&type=RPC&version=2020-04-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeCertificateState|要执行的操作。取值：**DescribeCertificateState**。 |
|OrderId|Long|是|123451222|要查询的证书申请订单的ID。

 **说明：** 您在调用[CreateCertificateForPackageRequest](~~204087~~)、[CreateCertificateRequest](~~164105~~)、[CreateCertificateWithCsrRequest](~~178732~~)接口提交证书申请后，可以从请求返回数据中获取对应的证书申请订单ID（即**OrderId**）。 |

调用API时，除了本文中该API的请求参数，还需加入阿里云API公共请求参数。公共请求参数的详细介绍，请参见[公共参数](~~164108~~)。

调用API的请求格式，请参见本文**示例**中的请求示例。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|082FAB35-6AB9-4FD5-8750-D36673548E76|本次请求的ID。 |
|Type|String|domain\_verify|证书申请订单的状态。取值：

 -   **domain\_verify**：**待验证**，表示证书申请提交后，您还没有完成域名验证。

**说明：** 您在提交证书申请后，必须手动完成域名所有权验证，证书申请才可以进入审核环节。如果您还没有完成域名验证，则可以参照本接口的返回数据，完成域名验证。

-   **process**：**审核中**，表示证书申请处于CA中心审核环节。
-   **verify\_fail**：**审核失败**，表示证书申请审核失败。

**说明：** 审核失败可能是因为您提交的证书申请信息不正确，建议您调用[DeleteCertificateRequest](~~164109~~)删除审核失败的订单（已删除订单不会消耗证书资源包个数），并重新提交证书申请。

-   **certificate**：**已签发**，表示证书已经签发。 |
|ValidateType|String|FILE|提交证书申请时选择的域名验证方式。取值：

 -   **DNS**： 表示DNS验证。通过在域名的DNS管理平台为域名添加指定的DNS解析记录，验证域名的所有权。
-   **FILE**：表示文件验证。通过在域名服务器上创建指定的文件，验证域名的所有权。

 **说明：** 仅当**Type**取值为**domain\_verify**（表示域名验证环节），才会返回该参数。 |
|RecordDomain|String|\_dnsauth|使用DNS验证方式进行域名验证时，您需要操作的主机记录。

 **说明：** 仅当**Type**取值为**domain\_verify**（表示域名验证环节）且**ValidateType**取值为**DNS**（表示验证方式为DNS验证）时，才会返回该参数。 |
|RecordType|String|TXT|使用DNS验证方式进行域名验证时，您需要添加的解析记录的类型。取值：

 -   **TXT**：表示文本记录。
-   **CNAME**：表示别名记录。

 **说明：** 仅当**Type**取值为**domain\_verify**（表示域名验证环节）且**ValidateType**取值为**DNS**（表示验证方式为DNS验证）时，才会返回该参数。 |
|RecordValue|String|20200420000000223erigacv46uhaubchcm0o7spxi7i2isvjq59mlx9lucnkqcy|使用DNS验证方式进行域名验证时，您需要添加的解析记录的记录值。

 **说明：** 仅当**Type**取值为**domain\_verify**（表示域名验证环节）且**ValidateType**取值为**DNS**（表示验证方式为DNS验证）时，才会返回该参数。 |
|Domain|String|www.example.com|使用文件验证方式进行域名验证时，待验证的域名。您需要连接该域名对应的服务器，并在服务器上创建指定的文件（即**Uri**）。

 **说明：** 仅当**Type**取值为**domain\_verify**（表示域名验证环节）且**ValidateType**取值为**FILE**（表示验证方式为文件验证）时，才会返回该参数。 |
|Uri|String|/.well-known/pki-validation/fileauth.txt|使用文件验证方式进行域名验证时，您需要在域名服务器中创建的文件。**Uri**包含文件路径及名称。

 **说明：** 仅当**Type**取值为**domain\_verify**（表示域名验证环节）且**ValidateType**取值为**FILE**（表示验证方式为文件验证）时，才会返回该参数。 |
|Content|String|http://example.com/.well-known/pki-validation/fileauth.txt|使用文件验证方式进行域名验证时，您需要在新创建文件中写入的内容。

 **说明：** 仅当**Type**取值为**domain\_verify**（表示域名验证环节）且**ValidateType**取值为**FILE**（表示验证方式为文件验证）时，才会返回该参数。 |
|Certificate|String|——BEGIN CERTIFICATE—— …… ——END CERTIFICATE——|证书内容（PEM格式）。关于PEM格式的更多介绍以及如何进行证书格式转换，请参见[主流数字证书都有哪些格式？](~~42214~~)。

 **说明：** 仅当**Type**取值为**certificate**（表示证书已经签发）时，才会返回该参数。 |
|PrivateKey|String|——BEGIN RSA PRIVATE KEY—— …… ——END RSA PRIVATE KEY——|证书私钥内容（PEM格式）。关于PEM格式的更多介绍以及如何进行证书格式转换，请参见[主流数字证书都有哪些格式？](~~42214~~)。

 **说明：** 仅当**Type**取值为**certificate**（表示证书已经签发）时，才会返回该参数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeCertificateState
&OrderId=123451222
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DescribeCertificateStateResponse>
    <RequestId>082FAB35-6AB9-4FD5-8750-D36673548E76</RequestId>
    <Type>domain_verify</Type>
    <ValidateType>FILE</ValidateType>
    <Domain>www.example.com</Domain>
    <Uri>/.well-known/pki-validation/fileauth.txt</Uri>
    <Content>http://example.com/.well-known/pki-validation/fileauth.txt</Content>
</DescribeCertificateStateResponse>
```

`JSON`格式

```
{
  "RequestId":"082FAB35-6AB9-4FD5-8750-D36673548E76",
  "Type": "domain_verify",
  "ValidateType": "FILE",
  "Domain": "www.example.com",
  "Uri": "/.well-known/pki-validation/fileauth.txt",
  "Content": "http://example.com/.well-known/pki-validation/fileauth.txt"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

