# CreateDVOrderAudit

Submits a Domain Validation \(DV\) certificate application.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=cas&api=CreateDVOrderAudit&type=RPC&version=2018-07-13)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateDVOrderAudit|The operation that you want to perform. Set the value to **CreateDVOrderAudit**. |
|City|String|Yes|hangzhou|The city of the applicant. We recommend that you set this parameter in Chinese Pinyin.

 **Note:** This parameter is the information that you must provide during the certificate application process. Alibaba Cloud cannot obtain this information. Therefore, you must manually enter it. |
|Domain|String|Yes|\*.com|The domain name that you want the certificate to protect. If you want to protect multiple domain names, separate them with commas \(,\).

 **Note:** This parameter is the information that you must provide during the certificate application process. Alibaba Cloud cannot obtain this information. Therefore, you must manually enter it. |
|DomainVerifyType|String|Yes|DNS|The method to verify the identity of the registrant. Valid values:

 -   **FILE**: file verification. Alibaba Cloud verifies the ownership of your domain name after you create a specific file on your DNS server.
-   **DNS**: DNS verification. Add a record for the domain name in its DNS system.

**Note:** This parameter is the information that you must provide during the certificate application process. Alibaba Cloud cannot obtain this information. Therefore, you must manually enter it. |
|Email|String|Yes|\*@xx.com|The contact email.

 **Note:** This parameter is the information that you must provide during the certificate application process. Alibaba Cloud cannot obtain this information. Therefore, you must manually enter it. |
|InstanceId|String|Yes|cas-cn-68n1mm16\*\*\*\*|The ID of the SSL Certificates Service instance.

 **Note:** This parameter is the information that you must provide during the certificate application process. Alibaba Cloud cannot obtain this information. Therefore, you must manually enter it. |
|Mobile|String|Yes|1335678\*\*\*\*|The contact phone number.

 **Note:** This parameter is the information that you must provide during the certificate application process. Alibaba Cloud cannot obtain this information. Therefore, you must manually enter it. |
|Province|String|Yes|zhejiang|The province of the applicant. We recommend that you set this parameter in Chinese Pinyin.

 **Note:** This parameter is the information that you must provide during the certificate application process. Alibaba Cloud cannot obtain this information. Therefore, you must manually enter it. |
|Username|String|Yes|AXXX|The name of the contact.

 **Note:** This parameter is the information that you must provide during the certificate application process. Alibaba Cloud cannot obtain this information. Therefore, you must manually enter it. |
|SourceIp|String|No|1.2.3.4|The source IP address of the request. |
|Lang|String|No|zh|The language of the request and response. Valid values:

 -   **zh**: Chinese
-   **en**: English |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|5D97F21E-2B95-4EA9-8A9B-2759E04A5B4C|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=CreateDVOrderAudit
&City=hangzhou
&Domain=*.com
&DomainVerifyType=DNS
&Email=*@xx.com
&InstanceId=cas-cn-68n1mm16****
&Mobile=1335678****
&Province=zhejiang
&Username=AXXX
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateDVOrderAuditResponse>
	  <RequestId>5D97F21E-2B95-4EA9-8A9B-2759E04A5B4C</RequestId>
</CreateDVOrderAuditResponse>
```

`JSON` format

```
{
	"RequestId": "5D97F21E-2B95-4EA9-8A9B-2759E04A5B4C"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/cas).

