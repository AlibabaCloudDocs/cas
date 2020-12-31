# CreateCertificateRequest

调用CreateCertificateRequest完成扩展服务DV证书的购买、申请和签发流程。针对批量购买证书的场景，证书扩展服务可通过调用该API实现DV证书下单购买与申请证书一步完成。

**说明：** 您购买了证书扩展服务后，才可以使用该API。具体请参见[证书扩展服务](~~165099~~)。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=CreateCertificateRequest&type=RPC&version=2020-04-07)

## 请求参数

|名称|位置|类型|是否必选|示例值|描述|
|--|--|--|----|---|--|
|Action|Query|String|是|CreateCertificateRequest|要执行的操作。取值：**CreateCertificateRequest**。 |
|Domain|Query|String|是|www.aliyun.com|申请证书时绑定的域名。 |
|Email|Query|String|是|example@aliyun.com|申请人邮箱。 |
|Phone|Query|String|是|1381111\*\*\*\*|申请人手机号。 |
|Username|Query|String|是|keller|申请人姓名。 |
|ValidateType|Query|String|是|DNS|域名所有权验证方式。取值：

 -   **FILE**：文件验证，通过在您域名服务器上创建指定文件来验证该域名的所有权。
-   **DNS**：手动DNS验证。如果您需要保护的域名是非阿里云域名，您需要到该域名的管理平台中为该域名添加一条TXT类型的DNS记录。例如：如果您购买的是A公司的域名，您需要到A公司的域名管理平台添加DNS记录文件。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CBF1E9B7-D6A0-4E9E-AD3E-2B47E6C2837D|阿里云为该请求生成的唯一标识符。 |
|OrderId|Long|98987582437920968|订单证书ID。 |

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

`XML` 格式

```
<CreateCertificateRequestResponse>
    <RequestId>082FAB35-6AB9-4FD5-8750-D36673548E76</RequestId>
    <OrderId>1</OrderId>
</CreateCertificateRequestResponse>
```

`JSON` 格式

```
{
  "RequestId":"082FAB35-6AB9-4FD5-8750-D36673548E76",
  "OrderId": 1
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

