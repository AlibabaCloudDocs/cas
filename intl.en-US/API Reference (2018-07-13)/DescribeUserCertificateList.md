# DescribeUserCertificateList

Queries certificates.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=cas&api=DescribeUserCertificateList&type=RPC&version=2018-07-13)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeUserCertificateList|The operation that you want to perform. Set the value to **DescribeUserCertificateList**. |
|CurrentPage|Integer|Yes|1|The number of the page to return. Default value: 1. |
|ShowSize|Integer|Yes|50|The number of entries to return on each page. Default value: 50. |
|SourceIp|String|No|1.2.3.4|The source IP address of the request. |
|Lang|String|No|zh|The language of the request and response. Valid values:

 -   **zh**: Chinese
-   **en**: English |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|CertificateList|Array| |The returned certificates. |
|buyInAliyun|Boolean|true|Indicates whether the certificate was purchased from Alibaba Cloud. Valid values:

 -   **true**: The certificate was purchased from Alibaba Cloud.
-   **false**: The certificate was not purchased from Alibaba Cloud. |
|city|String|hongzhou|The city of the company or organization to which the user who purchased the certificate belongs. |
|common|String|\*.com|The primary domain name bound to the certificate. |
|country|String|CN|The country or region of the company or organization to which the user who purchased the certificate belongs. |
|endDate|String|2027-10-14|The expiration date of the certificate. |
|expired|Boolean|false|Indicates whether the certificate has expired. Valid values:

 -   **true**: The certificate has expired.
-   **false**: The certificate has not expired. |
|fingerprint|String|6DEB816DE48D5E7DE6D7FE92A6B620B13DDF\*\*\*\*|The fingerprint of the certificate. |
|id|Long|763762|The ID of the certificate. |
|issuer|String|Alibaba|The certificate authority \(CA\) that issues the certificate. |
|name|String|auto-test-23673|The name of the certificate. |
|orgName|String|Alibaba|The name of the company or organization to which the user who purchased the certificate belongs. |
|province|String|Zhejiang|The province of the company or organization to which the user who purchased the certificate belongs. |
|sans|String|\*.com|All domain names bound to the certificate. |
|startDate|String|2017-10-16|The issuance date of the certificate. |
|CurrentPage|Integer|1|The page number of the returned page. |
|RequestId|String|E865F6AD-0294-4A24-A58B-DAC6BE2BDD20|The ID of the request. |
|ShowSize|Integer|50|The number of entries returned per page. |
|TotalCount|Integer|60|The total number of returned entries. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=DescribeUserCertificateList
&CurrentPage=1
&ShowSize=50
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeUserCertificateListResponse>
	  <TotalCount>736</TotalCount>
	  <RequestId>E865F6AD-0294-4A24-A58B-DAC6BE2BDD20</RequestId>
	  <CertificateList>
		    <startDate>2017-10-16</startDate>
		    <expired>false</expired>
		    <common>*.jinxibei.com</common>
		    <buyInAliyun>true</buyInAliyun>
		    <endDate>2027-10-14</endDate>
		    <orgName>Alibaba</orgName>
		    <city>Hangzhou</city>
		    <country>CN</country>
		    <id>763762</id>
		    <fingerprint>6DEB816DE48D5E7DE6D7FE92A6B620B13DD3****</fingerprint>
		    <issuer>Alibaba</issuer>
		    <name>auto-test-23673</name>
		    <sans>*.jinxibei.com</sans>
		    <province>Zhejiang</province>
	  </CertificateList>
	  <ShowSize>1</ShowSize>
	  <CurrentPage>50</CurrentPage>
</DescribeUserCertificateListResponse>
```

`JSON` format

```
{
	"TotalCount": 736,
	"RequestId": "E865F6AD-0294-4A24-A58B-DAC6BE2BDD20",
	"CertificateList": [
		{
			"startDate": "2017-10-16",
			"expired": false,
			"common": "*.jinxibei.com",
			"buyInAliyun": true,
			"endDate": "2027-10-14",
			"orgName": "Alibaba",
			"city": "Hangzhou",
			"country": "CN",
			"id": 763762,
			"fingerprint": "6DEB816DE48D5E7DE6D7FE92A6B620B13DDF****",
			"issuer": "Alibaba",
			"name": "auto-test-23673",
			"sans": "*.jinxibei.com",
			"province": "Zhejiang"
		}
	],
	"ShowSize": 1,
	"CurrentPage": 50
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/cas).

