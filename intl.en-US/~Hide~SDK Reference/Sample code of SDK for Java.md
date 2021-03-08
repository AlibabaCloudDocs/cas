# Sample code of SDK for Java

This topic provides the sample code of SSL Certificates Service SDK for Java. This way, you can create a certificate signing request \(CSR\) for a domain name by calling the CreateCasExtractKey operation and import an SSL certificate to SSL Certificates Service by calling the SaveCasExtractCertificate operation.

## Limits

If you want to use the sample code in this topic, install Java SE Development Kit \(JDK\) 7 or later.

## Dependencies

To use SSL Certificates Service SDK for Java, you must add the following dependencies:

-   To add a dependency on the core library of Alibaba Cloud SDK for Java, use the following sample code:

    ```
    <dependency>
        <groupId>com.aliyun</groupId>
        <artifactId>aliyun-java-sdk-core</artifactId>
        <version>5.0.0</version>
    </dependency>
    ```

-   To add a dependency on a JSON parser, such as Fastjson, use the following sample code:

    ```
    <dependency>
        <groupId>com.alibaba</groupId>
        <artifactId>fastjson</artifactId>
        <version>1.2.68</version>
    </dependency>
    ```


You can use the following sample code to define public methods. Before you use the following code, replace `<yourAccessKey>` and `<yourAccessKeySecret>` with the actual AccessKey ID and AccessKey secret.

**Note:** You can view your AccessKey information on the [AccessKey Management](https://ram.console.aliyun.com/manage/ak) page in the Alibaba Cloud Management Console.

```
private String endPoint = "cas.aliyuncs.com";
private String productName = "cas";
private String regionId = "cn-hangzhou";
private String accessKeyId = "<yourAccessKey>";
private String accessKeySecret = "<yourAccessKeySecret>";
private CommonResponse getCommonResponse(CommonRequest request) throws Exception {
    DefaultProfile.addEndpoint(this.regionId, this.productName, this.endPoint);
    DefaultProfile profile = DefaultProfile.getProfile(this.regionId, this.accessKeyId, this.accessKeySecret);
    IAcsClient client = new DefaultAcsClient(profile);
    return client.getCommonResponse(request);
}
```

## Procedure

You can use SSL Certificates Service SDK for Java to call the CreateCasExtractKey and SaveCasExtractCertificate operations. To use SSL Certificates Service SDK for Java, perform the following steps:

1.  Call the CreateCasExtractKey operation to create a CSR for a domain name. For more information, see [CreateCasExtractKey](#section_g3m_kdx_t3n).
2.  After the CSR is created, submit your certificate application. After the certificate authority \(CA\) approves your certificate application, you can obtain the corresponding certificate.

    **Note:** You cannot perform this step by using SSL Certificates Service SDK for Java. You can submit a certificate application in the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas). For more information, see [Step 1: Fill in certificate application information](/intl.en-US/Issue Certificates/Apply for and validate certificates.md).

3.  Call the SaveCasExtractCertificate operation to import the certificate issued in the previous step to SSL Certificates Service for unified management. For more information, see [SaveCasExtractCertificate](#section_h97_3jo_6en).

## CreateCasExtractKey

Creates a CSR for a domain name.

**Request parameters**

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateCasExtractKey|The operation that you want to perform. Set the value to **CreateCasExtractKey**.|
|Algorithm|String|Yes|RSA\_2048|The type of the key algorithm. Set the value to **RSA\_2048**.|
|MainDomain|String|Yes|example.com|The domain name to be bound to the certificate.|
|Sans|String|No|test1.example.com,test2.example.com|The subdomain name to be bound to the certificate. You can specify multiple subdomain names. If you specify multiple subdomain names, separate them with commas \(,\).|
|CountryCode|String|Yes|CN|The code of the country or region where the applicant is located. Specify this parameter in the format of abbreviation of international domain names. For example, the value CN indicates China.**Note:** This parameter is available only for applicants in China. If the applicant is in a region outside China, submit a [ticket](https://ticket-intl.console.aliyun.com/#/ticket/add/?productId=80). |
|Province|String|Yes|Zhejiang|The province where the applicant is located, in pinyin. For example, the value Zhejiang indicates Zhejiang Province.|
|Locality|String|Yes|Hangzhou|The city where the applicant is located, in pinyin. For example, the value Hangzhou indicates Hangzhou.|
|CorpName|String|No|xx Co. Ltd.|The name of the company where the applicant works.|
|Department|String|No|IT|The department of the company where the applicant works.|
|Email|String|No|tom@example.com|The email address of the applicant.|

**Response parameters**

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Csr|String|-----CSR content-----|The generated CSR content.|

**Sample code**

**Note:** Before you use the following code, replace the sample values of the request parameters with the actual parameter values.

```
public void testCasExtractCreateCsr() throws Exception {
    CommonRequest request = new CommonRequest();
    request.setSysAccept(FormatType.JSON);
    request.setSysProduct("cas");
    request.setSysAction("CreateCasExtractKey");
    request.setSysVersion("2020-12-03");
    request.setSysConnectTimeout(new Integer(3000));
    request.setSysReadTimeout(new Integer(5000));
    request.setSysMethod(MethodType.POST);
    request.putQueryParameter("Algorithm", "RSA_2048");
    request.putQueryParameter("MainDomain", "example.com");
    request.putQueryParameter("Sans", "test1.example.com,test2.example.com");
    request.putQueryParameter("CountryCode", "CN");
    request.putQueryParameter("Province", "Zhejiang");
    request.putQueryParameter("Locality", "Hangzhou");
    request.putQueryParameter("CorpName", "xx Co. Ltd.");
    request.putQueryParameter("Department", "IT");
    request.putQueryParameter("Email", "tom@example.com");
    CommonResponse response = this.getCommonResponse(request);
    String body = response.getData();
    JSONObject jsonObject = JSON.parseObject(body);
    String csr = jsonObject.getString("Csr");
    System.out.println(csr);
}
```

## SaveCasExtractCertificate

Imports an SSL certificate to SSL Certificates Service.

**Request parameters**

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Ation|String|Yes|SaveCasExtractCertificate|The operation that you want to perform. Set the value to **SaveCasExtractCertificate**.|
|Certificate|String|Yes|--BEGIN CERTIFICATE--...--END CERTIFICATE--|The certificate content to be imported. The content must meet the following requirements:-   The certificate content must match the CSR content generated by calling the [CreateCasExtractKey](#section_g3m_kdx_t3n) operation. Otherwise, the certificate content cannot be imported.
-   The certificate content must be in the following Privacy Enhanced Mail \(PEM\) format.

    ```
--BEGIN CERTIFICATE--
...
--END CERTIFICATE--
    ``` |

**Response parameters**

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|CertName|String|myCert|The name of the certificate.|
|CertId|String|1|The ID of the certificate.|

**Sample code**

**Note:** Before you use the following code, replace the sample values of the request parameters with the actual parameter values.

```
public void testCasExtractSaveCertificate() throws Exception {
    CommonRequest request = new CommonRequest();
    request.setSysAccept(FormatType.JSON);
    request.setSysProduct("cas");
    request.setSysAction("SaveCasExtractCertificate");
    request.setSysVersion("2020-12-03");
    request.setSysConnectTimeout(new Integer(3000));
    request.setSysReadTimeout(new Integer(5000));
    request.setSysMethod(MethodType.POST);
    String certificate = "--BEGIN CERTIFICATE--...--END CERTIFICATE--";
    request.putQueryParameter("Certificate", certificate);
    CommonResponse response = this.getCommonResponse(request);
    String body = response.getData();
    System.out.println(body);
    JSONObject jsonObject = JSON.parseObject(body);
    String certName = jsonObject.getString("CertName");
    long certId = jsonObject.getLongValue("CertId");

}
```

## Error codes

|Error code|Description|
|----------|-----------|
|-202012031|The error code returned because a required parameter is not specified.|
|-202012034|The error code returned because the format of the certificate is invalid.|
|-202012035|The error code returned because the certificate has been saved.|
|-202012036|The error code returned because the corresponding CSR content does not exist.|
|-202012037|The error code returned because the certificate content does not match the expected CSR content.|

