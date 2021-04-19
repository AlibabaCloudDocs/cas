# CreateUserCertificate

Uploads a certificate.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=cas&api=CreateUserCertificate&type=RPC&version=2018-07-13)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateUserCertificate|The operation that you want to perform. Set the value to **CreateUserCertificate**. |
|Cert|String|Yes|---BEGIN CERTIFICATE----- MIIF...... -----END CERTIFICATE-----|The certificate content in PEM format. |
|Key|String|Yes|---BEGIN RSA PRIVATE KEY----- MII.... -----END RSA PRIVATE KEY-----|The private key of the certificate in PEM format. |
|Name|String|Yes|auto-test-AXX|The custom certificate name.

 **Note:** The name must be unique within an Alibaba Cloud account. |
|SourceIp|String|No|1.2.3.4|The source IP address of the request. |
|Lang|String|No|ZH|The language of the request and response. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|CertId|Long|321|The ID of the certificate. |
|RequestId|String|BDXXX|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=CreateUserCertificate
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateUserCertificateResponse>
	  <RequestId>15BE9F82-71D1-4A83-9002-381C0BE2A889</RequestId>
	  <HostId>cas.aliyuncs.com</HostId>
	  <Code>200</Code>
</CreateUserCertificateResponse>
```

`JSON` format

```
{
	"RequestId": "15BE9F82-71D1-4A83-9002-381C0BE2A889",
	"HostId": "cas.aliyuncs.com",
	"Code": "200"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/cas).

