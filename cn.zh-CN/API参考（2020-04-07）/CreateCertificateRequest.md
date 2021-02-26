# CreateCertificateRequest

调用CreateCertificateRequest提交DV证书申请。调用本接口时，SSL证书服务将自动为您创建CSR文件。

**说明：** 本接口仅用于申请DV证书，不支持用于申请OV证书。推荐您使用[CreateCertificateForPackageRequest](~~204087~~)接口提交证书申请（可用于申请所有规格的证书，且支持选择CSR生成方式）。

调用本接口提交证书申请并成功签发证书后，将会消耗您已购买的对应规格的证书资源包的个数。您在发起请求时，可以通过**ProductCode**参数指定要申请的证书规格。

关于使用证书资源包API申请证书的完整流程，请参见[使用API申请证书的流程](~~204741~~)。

发起请求前，请确保您已购买对应规格的证书资源包。关于如何购买证书资源包，请参见[购买证书资源包](~~188316~~)。您可以调用[DescribePackageState](~~164110~~)查询指定规格的证书资源包的使用概况，包含已购买该规格证书资源包的总数、已提交证书申请的次数、成功签发证书的次数。

调用本接口提交证书申请后，您还需要调用[DescribeCertificateState](~~164111~~)接口，获取完成域名验证所需要的信息，并在域名的DNS管理平台（DNS验证方式）或者域名服务器（文件验证方式）手动完成验证，然后证书申请订单才会进入CA中心审核环节。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=CreateCertificateRequest&type=RPC&version=2020-04-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateCertificateRequest|要执行的操作。取值：**CreateCertificateRequest**。 |
|Domain|String|是|www.aliyun.com|证书要绑定的域名。仅支持设置一个域名。

 **说明：** 该域名必须与您要申请的证书规格（通过**ProductCode**参数指定）匹配。申请单域名证书时，此处必须设置一个单域名（例如，`www.aliyun.com`）；申请通配符域名证书时，此处必须设置一个通配符域名（例如，`*.aliyun.com`）。 |
|Email|String|是|example@aliyun.com|申请联系人的邮箱地址。 |
|Phone|String|是|1381111\*\*\*\*|申请联系人的手机号码。 |
|Username|String|是|keller|申请联系人的姓名。 |
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
|RequestId|String|CBF1E9B7-D6A0-4E9E-AD3E-2B47E6C2837D|本次请求的ID。 |
|OrderId|Long|98987582437920968|本次证书申请订单的ID。

 **说明：** 后续您可以使用该ID查询证书申请订单的状态，具体操作，请参见[DescribeCertificateState](~~164111~~)。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateCertificateRequest
&Domain=www.aliyun.com
&Email=example@aliyun.com
&Phone=1381111****
&Username=keller
&ValidateType=DNS
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<CreateCertificateRequestResponse>
    <RequestId>082FAB35-6AB9-4FD5-8750-D36673548E76</RequestId>
    <OrderId>98987582437920968</OrderId>
</CreateCertificateRequestResponse>
```

`JSON`格式

```
{
  "RequestId":"082FAB35-6AB9-4FD5-8750-D36673548E76",
  "OrderId": 98987582437920968
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

