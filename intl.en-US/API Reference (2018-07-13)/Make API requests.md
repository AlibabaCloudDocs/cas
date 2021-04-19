# Make API requests

To send an SSL Certificates Service API request, you must send an HTTP GET request to the SSL Certificates Service endpoint. You must add the request parameters that correspond to the API operation being called. After you call the API operation, the system returns a response. The request and response are encoded in UTF-8.

## Request syntax

SSL Certificates Service API operations use the RPC protocol. You can call SSL Certificates Service API operations by sending HTTP GET requests.

Use the following request syntax when you send an API request:

```
https://Endpoint/?Action=xx&Parameters
```

where:

-   Endpoint: the endpoint of the SSL Certificates Service API is cas.aliyuncs.com.
-   Action: the name of the operation being performed. For example, to query certificates, you must set the Action parameter to DescribeUserCertificateList.
-   Version: the version number of the API. The current version of the SSL Certificates Service API is 2018-07-13.
-   Parameters: the request parameters for the operation. Separate multiple parameters with ampersands \(&\).

    Request parameters include both common parameters and operation-specific parameters. Common parameters include the information such as the API version number and authentication information. For more information, see [Common parameters](/intl.en-US/API Reference (2018-07-13)/Common parameters.md).


The following code shows an example on how to call the DescribeUserCertificateList operation to query certificates:

**Note:** All code in this topic is formatted to facilitate reading.

```
http(s)://cas.aliyuncs.com/?Action=DescribeUserCertificateList
&Format=xml
&Version=2018-07-13
&Signature=xxxx%xxxx%3D
&SignatureMethod=HMAC-SHA1
&SignatureNonce=15215528852396
&SignatureVersion=1.0
&AccessKeyId=key-test
&TimeStamp=2012-06-01T12:00:00Z
...
```

## Signature method

You must sign all API requests to ensure security. Alibaba Cloud uses the request signature to verify the identity of the API caller.

SSL Certificates Service implements symmetric encryption with an AccessKey pair to verify the identity of the request sender. An AccessKey pair is an identity credential issued to Alibaba Cloud accounts and RAM users, which is similar to a logon username and password. An AccessKey pair consists of an AccessKey ID and an AccessKey secret. The AccessKey ID is used to verify the identity of the user, whereas the AccessKey secret is used to encrypt and verify the signature string. You must keep your AccessKey secret strictly confidential.

You must add a signature string to an SSL Certificates Service API request in the following format:

```
https://endpoint/?SignatureVersion=1.0&SignatureMethod=HMAC-SHA1&Signature=CT9X0VtwR86fNWSnsc6v8YGOjuE%3D&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
```

Take the DescribeUserCertificateList operation as an example. Assume that the AccessKey ID is `testid` and the AccessKey secret is `testsecret`. The following code shows an example of the original request URL:

```
https://cas.aliyuncs.com/?Action=DescribeUserCertificateList
&TimeStamp=2016-02-23T12:46:24Z
&Format=XML
&AccessKeyId=testid
&SignatureMethod=HMAC-SHA1
&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
&Version=2018-07-13
&SignatureVersion=1.0
```

Perform the following operations to calculate the signature:

1.  Use the request parameters to create a string-to-sign.

    ```
    GET&%2F&AccessKeyId%3Dtestid&Action%3DDescribeUserCertificateList&Format%3DXML&SignatureMethod%3DHMAC-SHA1&SignatureNonce%3D3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf&SignatureVersion%3D1.0&TimeStamp%3D2016-02-23T12%253A46%253A24Z&Version%3D2018-12-03
    ```

2.  Calculate the HMAC value of the string-to-sign.

    Append an ampersand \(&\) to the AccessKey secret as the key to calculate the HMAC value. In this example, the key is `testsecret&`.

    ```
    CT9X0VtwR86fNWSnsc6v8YGOjuE=
    ```

3.  Add the signature string to the request as the Signature parameter.

    ```
    https://cas.aliyuncs.com/?Action=DescribeUserCertificateList
    &TimeStamp=2016-02-23T12:46:24Z
    &Format=XML
    &AccessKeyId=testid
    &SignatureMethod=HMAC-SHA1
    &SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
    &Version=2018-07-13
    &SignatureVersion=1.0
    &Signature=CT9X0VtwR86fNWSnsc6v8YGOjuE%3D
    ```


**Note:** Alibaba Cloud offers SDKs for multiple programming languages and third-party SDKs to help you calculate the signature. For more information about Alibaba Cloud SDKs, see [Alibaba Cloud SDKs](https://www.alibabacloud.com/zh/support/developer-resources?spm=a2c5t.10695662.1996646101.searchclickresult.7e6c5b4fbkB1Id).

