# DescribeDVOrderResult

Queries the detailed information of a Domain Validation \(DV\) certificate order.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=cas&api=DescribeDVOrderResult&type=RPC&version=2018-07-13)

## Request parameters

|Parameter|Position|Type|Required|Example|Description|
|---------|--------|----|--------|-------|-----------|
|Action|Query|String|Yes|DescribeDVOrderResult|The operation that you want to perform. Set the value to **DescribeDVOrderResult**. |
|InstanceId|Query|String|Yes|cas-cn-68n1mm16\*\*\*\*|The ID of the SSL Certificates Service instance associated with the certificate. |
|SourceIp|Query|String|No|1.2.3.4|The source IP address of the request. |
|Lang|Query|String|No|zh|The language of the request and response. Valid values:

 -   **zh**: Chinese
-   **en**: English |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Certificate|String|-----BEGIN CERTIFICATE----- MIIF...... -----END CERTIFICATE-----|If the value of **OrderStatus** is **issued**, the certificate is returned in PEM format. |
|CheckName|String|\_xx.aliyundns2018\*\*\*\*.certificatestests.com|If the value of **OrderStatus** is **checking**, the verification item is returned. |
|CheckType|String|DNS|If the value of **OrderStatus** is **checking**, the type of the verification item returned. Valid values:

 -   **DNS**: manual DNS verification. If you want to protect a domain name that is not hosted on Alibaba Cloud, you must manually add a TXT record for the domain name on its management platform. For example, if you purchase a domain name from Company A, you must manually add the DNS record on the management platform of Company A.
-   **FILE**: file verification. Alibaba Cloud verifies the ownership of your domain name after you create a specific file on your DNS server. |
|CheckValue|String|201810150000000k09v6d4........|If the value of **OrderStatus** is **checking**, the value of the verification item is returned. |
|OrderStatus|String|checking|The status of the order. Valid values:

 -   **checking**: indicates that the order is under review.
-   **issued**: indicates that the order has been issued.
-   **checked\_fail**: indicates that the order review failed. |
|PrivateKey|String|----BEGIN RSA PRIVATE KEY----- MII.... -----END RSA PRIVATE KEY-----|If the value of **OrderStatus** is **issued**, the private key of the certificate is returned in PEM format. |
|RequestId|String|EECA10D5-BD0F-4EF1-B3EA-B4578E5C6F8E|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=DescribeDVOrderResult
&InstanceId=cas-cn-68n1mm16****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeDVOrderResultResponse>
	  <CheckValue>201810150000000k09v6d49sb26ys9whgpjp7cdavl6ik8a1nfct9mnep68n0h31</CheckValue>
	  <OrderStatus>checking</OrderStatus>
	  <CheckType>DNS</CheckType>
	  <RequestId>EECA10D5-BD0F-4EF1-B3EA-B4578E5C6F8E</RequestId>
	  <CheckName>***.aliyundns2018****.certificatestests.com</CheckName>
</DescribeDVOrderResultResponse>
```

`JSON` format

```
{
    "CheckValue": "201810150000000k09v6d49sb26ys9whgpjp7cdavl6ik8a1nfct9mnep68n0h31",
    "OrderStatus": "checking",
    "CheckType": "DNS",
    "RequestId": "EECA10D5-BD0F-4EF1-B3EA-B4578E5C6F8E",
    "CheckName": "***.aliyundns2018****.certificatestests.com"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/cas).

