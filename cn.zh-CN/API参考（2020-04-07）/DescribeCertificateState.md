# DescribeCertificateState

调用DescribeCertificateState查询DV证书的申请状态。

**说明：** 您购买了证书扩展服务后，才可以使用该API。具体请参见[证书扩展服务](~~165099~~)。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=DescribeCertificateState&type=RPC&version=2020-04-07)

## 请求参数

|名称|位置|类型|是否必选|示例值|描述|
|--|--|--|----|---|--|
|Action|Query|String|是|DescribeCertificateState|要执行的操作。取值：**DescribeCertificateState**。 |
|OrderId|Query|Long|是|123451222|证书订单ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Certificate|String|-----BEGIN CERTIFICATE----- MIIF...... -----END CERTIFICATE-----|当Type取值为**certificate**时，返回PEM格式证书。 |
|Content|String|http://hangzhou.com/.well-known/pki-validation/fileauth.txt|当Type取值为**domain\_verify**且ValidateType取值为**FILE**时，返回域名验证URL地址的URI的内容。 |
|Domain|String|www.hangzhou.com|当Type取值为**domain\_verify**且ValidateType取值为**FILE**时，返回待验证的域名。 |
|PrivateKey|String|123456abbca|当Type取值为**certificate**时，返回PEM格式证书私钥。 |
|RecordDomain|String|\_dnsauth|当Type取值为**domain\_verify**且ValidateType取值为**DNS**时，返回主机记录。 |
|RecordType|String|TXT|当Type取值为**domain\_verify**且ValidateType取值**DNS**时，返回验证记录类型。取值：

 -   **TXT**：文本记录
-   **CNAME**：别名记录 |
|RecordValue|String|20200420000000223erigacv46uhaubchcm0o7spxi7i2isvjq59mlx9lucnkqcy|当Type取值为**domain\_verify**且ValidateType取值为**DNS**时，返回记录值。 |
|RequestId|String|08F45EA0-66A7-4504-9B31-3589F5C\*\*\*\*\*|请求消息的ID。 |
|Type|String|process|证书申请状态类型。取值：

 -   **process**：表示证书正在申请中。
-   **verify\_fail**：表示证书申请失败。您可以删除申请失败的证书，删除后不占用已申请的证书数量。
-   **domain\_verify**：表示域名正在审核中。
-   **certificate**：表示证书已经签发。 |
|Uri|String|/.well-known/pki-validation/fileauth.txt|当Type取值为**domain\_verify**且ValidateType取值为**FILE**时，返回待验证的URI。 |
|ValidateType|String|DNS|当Type取值为**domain\_verify**时，返回提交证书申请时选择的验证方式。取值：

 -   **DNS**： 手动DNS验证。如果您需要保护的域名是非阿里云域名，您需要到该域名的管理平台中为该域名添加一条TXT类型的DNS记录。例如：如果您购买的是A公司的域名，您需要到A公司的域名管理平台添加DNS记录文件。
-   **FILE**：文件验证，通过在您域名服务器上创建指定文件来验证该域名的所有权。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeCertificateState
&OrderId=123451222
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeCertificateStateResponse>
    <RequestId>082FAB35-6AB9-4FD5-8750-D36673548E76</RequestId>
    <Type>domain_verify</Type>
    <ValidateType>FILE</ValidateType>
    <Domain>www.hangzhou.com</Domain>
    <Uri>/.well-known/pki-validation/fileauth.txt</Uri>
    <Content>http://hangzhou.com/.well-known/pki-validation/fileauth.txt</Content>
</DescribeCertificateStateResponse>
```

`JSON` 格式

```
{
  "RequestId":"082FAB35-6AB9-4FD5-8750-D36673548E76",
  "Type": "domain_verify",
  "ValidateType": "FILE",
  "Domain": "www.hangzhou.com",
  "Uri": "/.well-known/pki-validation/fileauth.txt",
  "Content": "http://hangzhou.com/.well-known/pki-validation/fileauth.txt"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

