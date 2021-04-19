# DescribeOrderInstanceList

Queries the SSL Certificates Service instances in your certificate order.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=cas&api=DescribeOrderInstanceList&type=RPC&version=2018-07-13)

## Request parameters

|Parameter|Position|Type|Required|Example|Description|
|---------|--------|----|--------|-------|-----------|
|Action|Query|String|Yes|DescribeOrderInstanceList|The operation that you want to perform. Set the value to **DescribeOrderInstanceList**. |
|StartIndex|Query|Integer|Yes|0|The start index number. The system starts to query the instance information of the certificate order from this index number. Set the value to **0**. |
|SourceIp|Query|String|No|1.2.3.4|The source IP address of the request. |
|Lang|Query|String|No|zh|The language of the request and response. Valid values:

 -   **zh**: Chinese
-   **en**: English |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|OrderList|Array of order| |The returned SSL Certificates Service instances. |
|CertType|String|OV|The type of the certificate. Valid values:

 -   **OV**: Organization Validation \(OV\) SSL certificates
-   **EV**: Extended Validation \(EV\) SSL certificates
-   **DV**: Domain Validation \(DV\) SSL certificates
-   **FREE**: free SSL certificates |
|Id|Long|2755629|The ID of the returned data source. |
|InstanceId|String|cas-cn-68n1mm16\*\*\*\*|The ID of the SSL Certificates Service instance. |
|Source|String|BUY|The source of the request for the certificate order. Valid values:

 -   **BUY**: indicates that the certificate order was from the SSL Certificates Service buy page.
-   **CDN**: indicates that the certificate order was from Alibaba Cloud CDN.
-   **OSS**: indicates that the certificate order was from Object Storage Service \(OSS\).
-   **EWS**: indicates that the certificate order was from a host service.
-   **DOMAIN**: indicates that the certificate order was from a domain name service. |
|Status|String|PAYED|The status of the certificate order. Valid values:

 -   **PAYED**: The order has been paid.
-   **CHECKING**: The certificate is being validated.
-   **Verifying**: The certificate is being verified.
-   **CHECKED\_FAIL**: The certificate verification failed.
-   **Pending Verification**: The certificate is to be verified.
-   **Pending Verification for Revocation**: The certificate revocation is to be verified.
-   **Verifying Revocation**: The certificate revocation is being verified.
-   **Issued**: The certificate has been issued. |
|RequestId|String|5BCD2F6C-7A9D-47C1-8588-2CC6A4E0BE5E|The ID of the request. |
|TotalCount|Integer|12|The total number of returned SSL Certificates Service instances. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=DescribeOrderInstanceList
&StartIndex=0
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeOrderInstanceListResponse>
	  <OrderList>
		    <Source>BUY</Source>
		    <Status>PAYED</Status>
		    <CertType>EV</CertType>
		    <InstanceId>cas-cn-68n1mm16****</InstanceId>
		    <Id>2755629</Id>
	  </OrderList>
	  <OrderList>
		    <Source>BUY</Source>
		    <Status>CHECKING</Status>
		    <CertType>OV</CertType>
		    <InstanceId>cas-cn-68n1mm16****</InstanceId>
		    <Id>2755619</Id>
	  </OrderList>
	  <TotalCount>145</TotalCount>
	  <RequestId>5BCD2F6C-7A9D-47C1-8588-2CC6A4E0BE5E</RequestId>
</DescribeOrderInstanceListResponse>
```

`JSON` format

```
{
	"OrderList": [
		{
			"Source": "BUY",
			"Status": "PAYED",
			"CertType": "EV",
			"InstanceId": "cas-cn-68n1mm16****",
			"Id": 2755629
		},
		{
			"Source": "BUY",
			"Status": "CHECKING",
			"CertType": "OV",
			"InstanceId": "cas-cn-68n1mm16****",
			"Id": 2755619
		}
	],
	"TotalCount": 145,
	"RequestId": "5BCD2F6C-7A9D-47C1-8588-2CC6A4E0BE5E"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/cas).

