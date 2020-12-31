# DescribePackageState

调用DescribePackageState查询已经购买的DV证书总数和使用情况。

**说明：** 您购买了证书扩展服务后，才可以使用该API。具体请参见[证书扩展服务](~~165099~~)。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=DescribePackageState&type=RPC&version=2020-04-07)

## 请求参数

|名称|位置|类型|是否必选|示例值|描述|
|--|--|--|----|---|--|
|Action|Query|String|是|DescribePackageState|要执行的操作。取值：**DescribePackageState**。 |
|ProductCode|Query|String|否|symantec-free-1-free|证书品牌类型。取值：

 -   **symantec-free-1-free**：免费单域名证书
-   **symantec-dv-1-starter**：Digicert DV通配符证书
-   **geotrust-dv-w-starter**：Geotrust DV通配符证书
-   **geotrust-dv-1-starter**：Geotrust DV单域名证书
-   **globalsign-dv-1-personal**：Globalsign DV单域名证书
-   **globalsign-dv-w-advanced**：Globalsign DV通配符证书 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|IssuedCount|Long|1|已经签发的DV证书的数量。 |
|ProductCode|String|symantec-free-1-free|证书品牌类型。取值：

 -   **symantec-free-1-free**：免费单域名证书
-   **symantec-dv-1-starter**：Digicert DV通配符证书
-   **geotrust-dv-w-starter**：Geotrust DV通配符证书
-   **geotrust-dv-1-starter**：Geotrust DV单域名证书
-   **globalsign-dv-1-personal**：Globalsign DV单域名证书
-   **globalsign-dv-w-advanced**：Globalsign DV通配符证书 |
|RequestId|String|08F45EA0-66A7-4504-9B31-3589F5CE308D|请求消息的ID。 |
|TotalCount|Long|10|已经购买的DV证书总数。 |
|UsedCount|Long|2|已经申请的DV证书数量。

 **说明：** 只要发起[CreateCertificateRequest](~~164105~~)请求就算已经申请了一张证书，不论是否签发。支持重复申请证书。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribePackageState
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribePackageStateResponse>
    <RequestId>082FAB35-6AB9-4FD5-8750-D36673548E76</RequestId>
    <TotalCount>1</TotalCount>
    <UsedCount>1</UsedCount>
    <IssuedCount>1</IssuedCount>
    <ProductCode>symantec-free-1-free</ProductCode>
</DescribePackageStateResponse>
```

`JSON` 格式

```
{
    "RequestId": "082FAB35-6AB9-4FD5-8750-D36673548E76",
    "TotalCount": "1",
    "UsedCount": "1",
    "IssuedCount": "1",
    "ProductCode": "symantec-free-1-free"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

