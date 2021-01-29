# DescribeOrderInstanceList

Query the list of certificates in a certificate order.

You can call this operation to query the list of certificates in your certificate order.

## Debugging

[Alibaba Cloud provides OpenAPI Explorer to simplify API usage. You can use OpenAPI Explorer to search for APIs, call APIs, and dynamically generate SDK example code.](https://api.aliyun.com/#product=cas&api=DescribeOrderInstanceList&type=RPC&version=2018-07-13)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeOrderInstanceList|The operation that you want to perform. Set this value to DescribeOrderInstanceList. |
|StartIndex|Integer|Yes|1|The start index number. This parameter specifies from which index number you start to query certificates in your certificate order. |
|Lang|String|No|zh|The language type of the request fields. |
|SourceIp|String|No|1.2.3.4|The source IP address of the request. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|OrderList| | |The list of returned certificates. |
|CertType|String|\*\*\* DV SSL|The type of the certificate. |
|Id|Long|1111100000|The ID of the returned data source. |
|InstanceId|String|cas-cn-v\*\*\*|The ID of the certificate. |
|Source|String|\*\*\*.test. \*\*\*|The source of the request for the certificate order. |
|Status|String|Paid|The status of the certificate order.

 Valid values:

 -   **Paid**: The order has been paid.
-   **Verifying**: The certificate is under review.
-   **Verification Failed**: The certificate verification failed.
-   **Pending Verification**: The certificate is to be verified.
-   **Pending Verification for Revocation**: The certificate revocation is to be verified.
-   **Verifying Revocation**: The certificate revocation is under review.
-   **Issued**: The certificate has been issued. |
|RequestId|String|EF69F215-B307-4A23-8890-D8171D3A51D3|The ID of the request. |
|TotalCount|Integer|0|The total number of returned certificates. |

## Examples

Sample request

```

http(s)://[Endpoint]/? Action=DescribeOrderInstanceList
&<Common request parameters>

```

Sample success response

`XML` format

```
<DescribeOrderInstanceList>
	  <TotalCount>0</TotalCount>
	  <RequestId>FACBE1FA-9316-4A58-AA95-B88E40B93A78</RequestId>
</DescribeOrderInstanceList>
```

`JSON` format

```
{
	"TotalCount":0,
	"OrderList":[],
	"RequestId":"EF69F215-B307-4A23-8890-D8171D3A51D3"
}
```

## Error codes

The operation returns only common errors. For more information about errors common to all operations, see [Error codes](https://error-center.alibabacloud.com/status/product/cas).

