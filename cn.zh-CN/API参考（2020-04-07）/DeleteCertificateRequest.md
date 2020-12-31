# DeleteCertificateRequest

调用DeleteCertificateRequest删除DV证书申请失败的订单。

**说明：** 您购买了证书扩展服务后，才可以使用该API。具体请参见[证书扩展服务](~~165099~~)。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=DeleteCertificateRequest&type=RPC&version=2020-04-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteCertificateRequest|要执行的操作。取值：**DeleteCertificateRequest**。 |
|OrderId|Long|是|123451222|证书订单ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|DD73CB0A-6E99-49AB-9569-5A\*\*\*\*\*\*|请求消息的ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteCertificateRequest
&OrderId=123451222
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DeleteCertificateRequestResponse>
    <RequestId>082FAB35-6AB9-4FD5-8750-D36673548E76</RequestId>
</DeleteCertificateRequestResponse>
```

`JSON` 格式

```
{
  "RequestId":"082FAB35-6AB9-4FD5-8750-D36673548E76"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

访问[错误中心](https://error-center.alibabacloud.com/status/product/cas)查看更多错误码。

|HttpCode

|错误码

|描述 |
|----------|-----|----|
|404

|NotFoundPackage

|没有购买套餐包。 |
|404

|NotRemainCount

|套餐中不可用的证书的数量。 |
|403

|CreateCertificateRequestFailed

|创建请求失败。 |
|404

|NotFoundOrder

|没有找到订单 。 |
|403

|OrderStateError

|订单状态错误。 |
|403

|DeleteFail

|删除失败 。 |
|500

|Error

|发生错误 。 |

