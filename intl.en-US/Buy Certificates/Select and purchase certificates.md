# Select and purchase certificates

Alibaba Cloud SSL Certificates Service supports different brands and types of certificates. This topic describes how to select and purchase an SSL certificate on Alibaba Cloud.

## Procedure

1.  Log on to the SSL Certificate console. On the SSL Certificates page, click [Purchase Certificate](https://common-buy-intl.aliyun.com/?commodityCode=cas_intl#/buy).

2.  Specify **Type of Domain** based on the domain names that you want to protect.

    We recommend that you specify Type of Domain before you specify Certificate Category and Select Brand.

    The following table describes the types of domain names that Alibaba Cloud SSL Certificates Service supports.

    |Domain name type|Application scenario|Domain name example|
    |----------------|--------------------|-------------------|
    |**Wildcard Domain**|If you want to protect a base domain name and all the subdomain names of a specific level under this base domain name, select **Wildcard Domain**. **Note:**

    -   A wildcard domain name starts with the wildcard asterisk \(\*\). When you apply for a wildcard certificate, add the wildcard asterisk \(\*\) before your domain name. For example, enter \*.aliyun.com.
    -   Wildcard certificates support peer matching. Details are as follows:
        -   First-level wildcard domain name: The base domain name of the wildcard domain name and its first-level subdomain names can be protected.

For example, if you enter a first-level wildcard domain name \*.aliyun.com, your wildcard certificate enables the HTTPS service for your base domain name aliyun.com by default. You do not need to take the application and approval processes on a separate certificate for the base domain name.

        -   Second- or lower-level wildcard domain name: Only the peer-level domain names can be protected, and the base domain name of the wildcard domain name cannot be protected.
|Examples:

    -   A certificate for a first-level wildcard domain name \(\*.aliyun.com\):

It protects the base domain name aliyun.com and its first-level subdomain names, such as a.aliyun.com, b.aliyun.com, and c.aliyun.com. The second- or lower-level subdomain names of the base domain name cannot be protected, such as 1.a.aliyun.com, 1.1.a.aliyun.com, 1.b.aliyun.com, and 1.1.b.aliyun.com.

    -   A certificate for a second-level wildcard domain name \(\*.a.aliyun.com\):

It protects all peer-level domain names of the wildcard domain name, such as 1.a.aliyun.com, 2.a.aliyun.com, and 3.a.aliyun.com. The lower-level subdomain names of the wildcard domain name cannot be protected, such as 1.1.a.aliyun.com and 2.1.a.aliyun.com. The base domain name of the wildcard domain name a.aliyun.com cannot be protected. |
    |**Single Domain**|If you want to protect only one base domain name or one subdomain name \(non-wildcard domain name\), select **Single Domain**. This type of certificate protects the following domain names:     -   Base domain name
    -   Subdomain name
|None|
    |**Multiple Domain**|If you want to protect multiple domain names, such as different levels of subdomain names under the same base domain name or different base domain names with their subdomain names, select **Multiple Domain**.     -   A DigiCert Extended Validation \(EV\) SSL certificate protects a minimum of five domain names \(no more than 100\).
    -   Other types of SSL certificates can protect a minimum of three domain names \(no more than 100\).
Alibaba Cloud multi-domain certificates allow you to append domain names. However, you must enter at least three domain names when you apply for a certificate for the first time. Otherwise, you cannot append domain names later.

Assume that you have purchased a multi-domain certificate to protect 10 domain names and that you entered three domain names in **Domains to Bind** and submitted the application for the certificate for the first time. If you want to protect more domain names, you only need to [Ticket](https://workorder-intl.console.aliyun.com/#/ticket/add/?productId=80). In this example, you can append up to seven domain names.

|A GeoTrust Organization Validated \(OV\) multi-domain SSL certificate protects multiple domain names, such as aliyun.com, a.aliyun.com, b.aliyun.com, 1.a.aliyun.com, abc.com, and 1.abc.com.|

    **Note:** After you purchase the certificate, you must enter the domain names that you want to protect and apply for the certificate. Alibaba Cloud verifies the number and type of the domain names that you specify. If you purchase a multi-domain SSL certificate, note the following points:

    -   As stipulated by CAs, if you enter only one domain name when you apply for the certificate for the first time, the certificate becomes a single-domain SSL certificate. Even if the certificate is a multi-domain SSL certificate while you purchase it, you cannot append domain names later.
    -   After you append domain names, the certificate is issued again. You must install the new certificate to protect the appended domain names. The expiration time and private key of the newly issued certificate are the same as those of the original certificate. The original certificate is still available.
    -   We recommend that you append all the remaining domain names at a time because the validity period of the new certificate is the same as that of the original certificate. The later the remaining domain names are appended, the shorter the validity period of the new certificate.
3.  Specify **Certificate Category**. Alibaba Cloud SSL Certificates Service provides OV SSL certificates. DV is short for Domain Validation.

    If you select different types of certificates, you must provide different materials for approval when you apply for the certificates. For more information, see [Required materials](/intl.en-US/Issue Certificates/Apply for a certificate.md).

    The following examples show how different types of certificates are displayed in the address bar of a browser:

4.  Specify **Region** for the certificate. Only Asia Pacific, EU, and Middle East regions are supported.

5.  Specify **Select Brand** for the certificate. For more information, see [Brands of certificates supported by Alibaba Cloud](#section_hfl_s09_ij2).

6.  Specify **Quantity** and **Duration Purchased**.

    -   **Quantity**: A maximum of 10 certificates can be purchased for each type.
    -   **Duration Purchased**: The validity period of a certificate, which is up to two years.
    **Note:**

    -   The validity period of an SSL certificate is one or two years. The validity period varies with the certificate type. Before your certificate expires, you must renew it and apply for the renewed certificate. Then, you can install the renewed certificate on your web servers. For more information, see [Manual renewal](/intl.en-US/Renew Certificates/Manual renewal.md). If you select one year, your certificate must undergo the application, approval, and installation processes once a year. If you select two years, the processes must be taken every two years. If you want to reduce the number of approval processes, select two years.
    -   The validity period of a certificate starts after the certificate is approved.
7.  Click **Buy Now** to complete the payment.


## What to do next

After you purchase an SSL certificate, you must apply for the certificate and submit the required materials. You can obtain the certificate only after your application is approved.

When you apply for a certificate, you must prepare the required materials, upload the electronic copies of the materials, and submit them for approval. For more information, see [Required materials](/intl.en-US/Issue Certificates/Apply for a certificate.md). After your application is approved, you can install the certificate on your web servers and Alibaba Cloud services.

## Certificate selection reference

|Certificate requirement|Optional certificate type|Optional brand|Domain name type and example|Number of protected domain names|Number of purchased certificates|Purchased duration|Purchase portal|
|-----------------------|-------------------------|--------------|----------------------------|--------------------------------|--------------------------------|------------------|---------------|
|One certificate is required to protect all subdomain names under a base domain name.|No limit|No limit|Wildcard Domain Example: \*.aliyun.com

|1|1|One or two years|-|
|One certificate is required to protect all subdomain names under a base domain name.|No limit|No limit|Wildcard Domain Example: \*.buy.aliyun.com

|1|1|One or two years|-|
|One certificate is required to protect one base domain name.|No limit|No limit|Single Domain Example: www.buy.aliyun.com

|1|1|One or two years|-|
|One certificate is required to protect five or more domain names, including first-, second-, or lower-level domain names.|OV or EV|No limit|Multiple Domain Examples:

-   www.market.aliyun.com
-   example.aliyun.com
-   example.aliyun1.com
-   example.aliyun2.com

|5|1|One or two years|-|
| |Professional OV and enhanced OV|The same brand must be selected for multiple certificates.|No limit. If you purchase multiple certificates, you must merge them into one certificate.|No limit|No limit|No limit|-|
| |Professional OV and enhanced EV|DigiCert|No limit. SSL certificates must support the ECC algorithm.|No limit|No limit|No limit|-|
| |Professional OV|GlobalSign|No limit. SSL certificates must support the ECC algorithm.|No limit|No limit|No limit|[Purchase link](https://common-buy.aliyun.com/?commodityCode=cas&request=%7B%22cer_type%22:%22personal%22,%22brand%22:%22globalsign%22,%22domain_type%22:%22all%22,%22domain_num%22:1,%22order_num%22:1,%22ord_time%22:%221:Year%22%7D)|

## Brands of certificates supported by Alibaba Cloud

The following table lists different brands of digital certificates that Alibaba Cloud can issue.

|Certificate brand|Description|Additional information|
|-----------------|-----------|----------------------|
|**DigiCert**|DigiCert \(former Symantec\) is the largest CA and the most trusted SSL certificate brand across the industry. All DigiCert certificates use industry-leading encryption technologies to provide enhanced security solutions for different websites and servers.|None|
|**CFCA**|China Financial Certification Authority \(CFCA\) is certified by WebTrust and complies with globally unified authentication standards. It is a member of CA/Browser Forum. Global Trust SSL Certificates are independently developed CFCA, the authoritative CA in China, and are fully recognized as Chinese approved certificates. CFCA provides 24/7 financial-level security services and a comprehensive risk insurance plan. CFCA provides the Certification Practice Statement \(CPS\) of the global trust system in Chinese to ensure that users can understand the rights and obligations of both parties.|**Note:** CFCA server certificates do not support Apple iOS 10.1 and earlier versions, or Android 6.0 and earlier versions. |
|**GeoTrust**|GeoTrust is the second-largest CA across the industry and also a leader in identity and trust authentication. GeoTrust uses a variety of advanced technologies to allow organizations and companies of all sizes to deploy SSL digital certificates at low costs for the authentication of various identities.|None|
|**GlobalSign**|GlobalSign is one of the earliest CAs across the industry. It has been committed to network security authentication and digital certificate services. GlobalSign is a trusted CA and SSL digital certificate provider.|None|
|**Entrust**|Entrust is a world-renowned CA that has established a trusted virtual environment. It allows users to conduct secure digital transactions and communication from all locations. Entrust provides trust services for websites, software developers, and individuals, including issuing SSL certificates that are used for website authentication and encryption. Among the Fortune Global 500 companies, more than 83% businesses use Entrust SSL certificates.|None|

**Note:** Different brands or CA vendors provide different types of certificates. For example, GlobalSign only provides professional OV certificates.

