# CreateUserCertificate

Add a certificate.

**You can call this operation to add a certificate.**

## Debugging

[Alibaba Cloud provides OpenAPI Explorer to simplify API usage. You can use OpenAPI Explorer to search for APIs, call APIs, and dynamically generate SDK example code.](https://api.aliyun.com/#product=cas&api=CreateUserCertificate&type=RPC&version=2018-07-13)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateUserCertificate|The operation that you want to perform. Set this value to CreateUserCertificate. |
|Cert|String|Yes|---BEGIN CERTIFICATE----- MIIF...... -----END CERTIFICATE-----|The certificate content. This parameter must be in the Privacy Enhanced Mail \(PEM\) format. |
|Key|String|Yes|---BEGIN RSA PRIVATE KEY----- MII.... -----END RSA PRIVATE KEY-----|The private key of the certificate. This parameter must be in the PEM format. |
|Name|String|Yes|auto-test-AXX|The name of the certificate, which is user-defined. The name of a certificate must be unique within a user account. |
|Lang|String|No|ZH|The language type of the request and response. |
|SourceIp|String|No|1.2.3.4|The source IP address of the request. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|CertId|Long|321|The ID of the certificate. |
|RequestId|String|BDXXX|The ID of the request. |

## Examples

Sample request

```

http(s)://[Endpoint]/? Action=CreateUserCertificate
&<Common request parameters>

```

Sample success response

`XML` format

```
<CreateUserCertificate>
	  <RequestId>15BE9F82-71D1-4A83-9002-381C0BE2A889</RequestId>
	  <HostId>cas.aliyuncs.com</HostId>
	  <Code>200</Code>
    </CreateUserCertificate>
```

`JSON` format

```
{
	"RequestId":"15BE9F82-71D1-4A83-9002-381C0BE2A889",
	"HostId":"cas.aliyuncs.com",
	"Code":"200"
}
```

## Error codes

The operation returns only common errors. For more information about errors common to all operations, see [Error codes](https://error-center.alibabacloud.com/status/product/cas).

