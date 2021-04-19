# DescribeUserCertificateDetail

Queries the detailed information of a single certificate, including the certificate name, certificate content, certificate private key, certificate authority \(CA\), certificate validity period, and certificate fingerprint.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=cas&api=DescribeUserCertificateDetail&type=RPC&version=2018-07-13)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeUserCertificateDetail|The operation that you want to perform. Set the value to **DescribeUserCertificateDetail**. |
|CertId|Long|Yes|12345|The ID of the certificate.

 **Note:** You can call [CreateUserCertificate](~~126557~~) to query the value of **CertId**. |
|SourceIp|String|No|1.2.3.4|The source IP address of the request. |
|Lang|String|No|zh|The language of the request and response. Valid values:

 -   **zh**: Chinese
-   **en**: English |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|BuyInAliyun|Boolean|true|Indicates whether the certificate was purchased from Alibaba Cloud. Valid values:

 -   **true**: The certificate was purchased from Alibaba Cloud.
-   **false**: The certificate was not purchased from Alibaba Cloud. |
|Cert|String|-----BEGIN CERTIFICATE----- MIIF...... -----END CERTIFICATE-----|The certificate content in PEM format. |
|City|String|hangzhou|The city of the company or organization to which the user who purchased the certificate belongs. |
|Common|String|\*.com|The primary domain name bound to the certificate. |
|Country|String|Chinese|The country or region of the company or organization to which the user who purchased the certificate belongs. |
|EndDate|String|2020-07-13|The expiration date of the certificate. |
|Expired|Boolean|false|Indicates whether the certificate has expired. Valid values:

 -   **true**: The certificate has expired.
-   **false**: The certificate has not expired. |
|Fingerprint|String|6DEB816DE48DF\*\*\*\*|The fingerprint of the certificate. |
|Id|Long|1|The ID of the certificate. |
|Issuer|String|Digicert|The CA that issues the certificate. |
|Key|String|-----BEGIN RSA PRIVATE KEY----- MII.... -----END RSA PRIVATE KEY-----|The private key content of the certificate in PEM format. |
|Name|String|cert-1|The name of the certificate. |
|OrgName|String|Alibaba|The name of the company or organization to which the user who purchased the certificate belongs. |
|Province|String|zhejiang|The province of the company or organization to which the user who purchased the certificate belongs. |
|RequestId|String|08F45EA0-66A7-4504-9B31-3589F5CE308D|The ID of the request. |
|Sans|String|\*.com|All domain names bound to the certificate. |
|StartDate|String|2018-07-13|The issuance date of the certificate. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=DescribeUserCertificateDetail
&CertId=12345
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeUserCertificateDetailResponse>
	  <RequestId>08F45EA0-66A7-4504-9B31-3589F5CE308D</RequestId>
</DescribeUserCertificateDetailResponse>
```

`JSON` format

```
{
	"RequestId": "08F45EA0-66A7-4504-9B31-3589F5CE308D"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/cas).

