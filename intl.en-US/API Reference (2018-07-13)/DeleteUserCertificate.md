# DeleteUserCertificate

Deletes expired certificate files.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=cas&api=DeleteUserCertificate&type=RPC&version=2018-07-13)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteUserCertificate|The operation that you want to perform. Set the value to **DeleteUserCertificate**. |
|CertId|Long|Yes|111111|The ID of the certificate that you want to delete.

**Note:** You can call [CreateUserCertificate](~~126557~~) to query the value of **CertId**. |
|SourceIp|String|No|1.2.3.4|The source IP address of the request. |
|Lang|String|No|zh|The language of the request and response. Valid values:

-   **zh**: Chinese
-   **en**: English |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|BDB81BA2-E1F5-4D08-A2DD-4BE2BF44C90E|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=DeleteUserCertificate
&CertId=111111
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteUserCertificateResponse>
      <RequestId>BDB81BA2-E1F5-4D08-A2DD-4BE2BF44C90E</RequestId>
</DeleteUserCertificateResponse>
```

`JSON` format

```
{
    "RequestId": "BDB81BA2-E1F5-4D08-A2DD-4BE2BF44C90E"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/cas).

