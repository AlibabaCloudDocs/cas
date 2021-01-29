# Common parameters

This topic describes the common parameters for API operations provided by SSL Certificates Service.

## Common request parameters

Common request parameters are request parameters that you must use when you call each API operation.

|Parameter|Type|Required|Description|
|:--------|:---|:-------|:----------|
|Format|String|No|The format of the response. Valid values: JSON, XML\(default\) |
|Version|String|Yes|The version number of the API, in the format of YYYY-MM-DD. Valid value: 2018-08-13 |
|AccessKeyId|String|Yes|The AccessKey ID of your Alibaba Cloud account that is used to access SSL Certificates Service.|
|Signature|String|Yes|The signature string of the current request.|
|SignatureMethod|String|Yes|The signature algorithm. Valid value: HMAC-SHA1 |
|Timestamp|String|Yes|The timestamp when the request is signed. Specify the time in the ISO 8601 standard in the `yyyy-MM-ddTHH:mm:ssZ` format. The time must be in UTC. For example, `2013-01-10T12:00:00Z` indicates January 10, 2013, 20:00:00 \(UTC+8\). |
|SignatureVersion|String|Yes|The signature algorithm version. The current version is 1.0.|
|SignatureNonce|String|Yes|A unique and randomly generated number used to prevent replay attacks. Users must use different numbers for different requests. |
|ResourceOwnerAccount|String|No|The name of the account that owns the resource to be accessed through this API request.|

**Examples**

```
https://cas.aliyuncs.com/
? Format=xml
&Version=2018-08-13
&Signature=Pc5WB8gokVn0xfeu%2FZV%2BiNM1dgI%3D
&SignatureMethod=HMAC-SHA1
&SignatureNonce=15215528852396
&SignatureVersion=1.0
&AccessKeyId=key-test
&Timestamp=2012-06-01T12:00:00Z
```

## Common response parameters

API responses use the HTTP response format where a status code of 2XX indicates a successful call and a status code of 4XX or 5XX indicates a failed call.

Response data can be returned in either the JSON or XML format. You can specify the response format when you are making the request. The default response format is XML.

Every response has a unique RequestId regardless of whether the call was successful or not.

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? > 
        <!--Response root node-->
        <API operation name+response>
            <!--Request ID-->
            <RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId>
            <!--Responses-->
        </API operation name+response>                    
    ```

-   JSON format

    ```
    {
        "RequestId":"4C467B38-3910-447D-87BC-AC049166F216",
        /*Responses*/
        }
    ```


