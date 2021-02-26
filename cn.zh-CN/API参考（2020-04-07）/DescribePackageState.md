# DescribePackageState

调用DescribePackageState查询指定规格的证书资源包的使用概况，包含已购买该规格证书资源包的总数、已提交证书申请的次数、成功签发证书的次数。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=DescribePackageState&type=RPC&version=2020-04-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribePackageState|要执行的操作。取值：**DescribePackageState**。 |
|ProductCode|String|否|symantec-free-1-free|要查询的证书资源包的规格（即证书规格）。取值：

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

调用API时，除了本文中该API的请求参数，还需加入阿里云API公共请求参数。公共请求参数的详细介绍，请参见[公共参数](~~164108~~)。

调用API的请求格式，请参见本文**示例**中的请求示例。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|IssuedCount|Long|1|已经成功签发该规格证书的数量。 |
|ProductCode|String|symantec-free-1-free|证书资源包的规格（即证书规格）。取值：

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
|RequestId|String|10CFA380-1C58-45C7-8075-06215F3DB681|本次请求的ID。 |
|TotalCount|Long|20|已购买该规格证书资源包的总数量。 |
|UsedCount|Long|2|已经提交该规格证书申请的次数。

 **说明：** 您只要成功调用一次[CreateCertificateForPackageRequest](~~204087~~)、[CreateCertificateRequest](~~164105~~)、[CreateCertificateWithCsrRequest](~~178732~~)接口，就表示提交了一次证书申请（不论证书是否成功签发）。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribePackageState
&ProductCode=symantec-free-1-free
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DescribePackageStateResponse>
	  <TotalCount>20</TotalCount>
	  <RequestId>10CFA380-1C58-45C7-8075-06215F3DB681</RequestId>
	  <ProductCode>symantec-free-1-free</ProductCode>
	  <UsedCount>2</UsedCount>
	  <IssuedCount>1</IssuedCount>
</DescribePackageStateResponse>
```

`JSON`格式

```
{
	"TotalCount": 20,
	"RequestId": "10CFA380-1C58-45C7-8075-06215F3DB681",
	"ProductCode": "symantec-free-1-free",
	"UsedCount": 2,
	"IssuedCount": 1
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

