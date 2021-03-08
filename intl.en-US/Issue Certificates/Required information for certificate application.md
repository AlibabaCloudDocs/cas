# Required information for certificate application

When you apply for Domain Validation \(DV\), Organization Validation \(OV\), and Extended Validation \(EV\) SSL certificates by using SSL Certificates Service, you must enter application information and upload materials for review based on certificate types. This topic lists the application information required for different types of certificates for your reference when you apply for a certificate.

For more information about how to apply for a certificate, see [Apply for a certificate](/intl.en-US/Issue Certificates/Apply for and validate certificates.md).

## Required application information for a DV SSL certificate

When you apply for a DV SSL certificate, you must set the parameters listed in the following table.

|Parameter|Description|
|---------|-----------|
|**Domains to Bind**|Enter the website domain name that the certificate is used to protect.Move the pointer over the ![question mark](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7541715161/p223930.png) icon to view the number and type of domain names supported, and obtain more help. The number and type of domain names supported are based on the specific configuration of the instance.

Considerations:

-   The domain name type must be the same as the value of **Type of Domain** \(Single Domain or Wildcard Domain\) that you selected when you purchase the certificate.
-   When you enter a wildcard domain name, be sure to add a wildcard character \(`*`\). An example is `*.yourwebsite.com`.
-   `.jp` domain names are not supported.
-   When you apply for a DV SSL certificate, you cannot enter `.gov` or `.edu` domain names because .gov is applicable to government agencies and .edu is applicable to educational institutions. We recommend that you purchase OV and EV SSL certificates to protect `.gov` and `.edu` domain names. |
|**Domain Verification Method**|Select a method to verify the identity of the registrant.If the domain name that you entered is shown on the **Domain Name List** page in the [Domains](https://dc.console.aliyun.com/next/#/domain/list/all-domain) console, **Automatic DNS Verification** is automatically selected and cannot be modified. This method allows Alibaba Cloud to automatically verify the domain name for you. You do not need to manually perform this operation.

If the domain name that you entered is not shown on the **Domain Name List** page in the [Domains](https://dc.console.aliyun.com/next/#/domain/list/all-domain) console, you can use one of the following methods:

-   **Manual DNS Verification**: This method requires you to log on to the Domains console and configure the domain name verification information to the domain name resolution list by adding a DNS resolution record of the TXT type. You must have administrative permissions on domain name resolution to complete verification.
-   **File Verification**: Alibaba Cloud verifies the ownership of your domain name after you create a specific file on your DNS server. You must have administrator permissions on the domain name server to complete verification.

For more information about the two verification methods, see [How do I configure domain name authorization?](/intl.en-US/Issue Certificates/FAQ/How do I configure domain name authorization?.md). |
|**Contact**|From the Contact drop-down list, select the contact \(including contact information such as the email address and mobile number\) for this certificate application.**Note:** For example, the CA may send a domain verification email to the email address specified for the contact that you select or call the specified mobile number to confirm validation. Therefore, make sure that the contact information is accurate and valid.

If you have not created a contact, click **Create Contact** to create one. SSL Certificates Service saves the created contact information for you to use next time. For more information about how to configure a new contact, see [Create a contact](/intl.en-US/Contact Management/Manage contacts.md). |
|**Location**|Select the city or region where the applicant is located.|
|**CSR Generation**|The Certificate Signing Request \(CSR\) file is the source file of your public key certificate and contains information about your server and organization that you must submit to the CA for review.The **Manual** switch is turned off by default, which indicates that SSL Certificates Service automatically generates a CSR file. You can download the certificate and private key after the certificate is issued. If you use the automatic generation method, no modification is required.

If you turn on the **Manual** switch, you must use OpenSSL or Keytool to manually generate a CRS file, and copy and paste the content of the CSR file to the **CSR File** field. For more information about how to create a CSR file, see [How do I create a CSR file?]().

**Note:**

-   Make sure that your CSR file is in the correct format. Otherwise, your certificate application may fail. We recommend that you use a CSR file that is automatically generated by SSL Certificates Service to ensure valid file content.
-   You cannot deploy certificates that use manually generated CSR files to Alibaba Cloud services.
-   You must securely store your private key when a CSR file is generated. An SSL certificate corresponds to a private key. If the private key is lost, the certificate becomes invalid. Alibaba Cloud is not responsible for storing your private key. If your private key is lost, you must re-purchase a digital certificate to replace the original one. |
|**CSR File**|This parameter must be set only after you turn on the **Manual** switch for **CSR Generation**. Enter the content of your CSR file.|

## Required application information for an OV SSL certificate

When you apply for an OV SSL certificate, you must set the parameters listed in the following table.

|Parameter|Description|
|---------|-----------|
|**Domains to Bind**|Enter the website domain name that the certificate is used to protect.Move the pointer over the ![question mark](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7541715161/p223930.png) icon to view the number and type of domain names supported, and obtain more help. The number and type of domain names supported are based on the specific configuration of the instance.

Considerations:

-   The domain name type must be the same as the value of **Type of Domain** \(Single Domain or Wildcard Domain\) that you selected when you purchase the certificate.
-   When you enter a wildcard domain name, be sure to add a wildcard character \(`*`\). An example is `*.yourwebsite.com`.
-   `.jp` domain names are not supported.
-   When you apply for a DV SSL certificate, you cannot enter `.gov` or `.edu` domain names because .gov is applicable to government agencies and .edu is applicable to educational institutions. We recommend that you purchase OV and EV SSL certificates to protect `.gov` and `.edu` domain names. |
|**Contact**|From the Contact drop-down list, select the contact \(including contact information such as the email address and mobile number\) for this certificate application.**Note:** For example, the CA may send a domain verification email to the email address specified for the contact that you select or call the specified mobile number to confirm validation. Therefore, make sure that the contact information is accurate and valid.

If you have not created a contact, click **Create Contact** to create one. SSL Certificates Service saves the created contact information for you to use next time. For more information about how to configure a new contact, see [Create a contact](/intl.en-US/Contact Management/Manage contacts.md). |
|**Company**|From the Contact drop-down list, select the company information of this certificate application, including the company name, phone number, address, and business license.If you have not created company information, click **Create Company Profile** to create company information. SSL Certificates Service saves the created company information for you to use next time. For more information about how to configure new company information, see [Create a company profile](/intl.en-US/Contact Management/Manage company profiles.md). |
|**Business License**|After a value is selected for **Company**, the uploaded business license picture in the company information is automatically selected. No modification is required.|
|**CSR Generation**|The Certificate Signing Request \(CSR\) file is the source file of your public key certificate and contains information about your server and organization that you must submit to the CA for review.The **Manual** switch is turned off by default, which indicates that SSL Certificates Service automatically generates a CSR file. You can download the certificate and private key after the certificate is issued. If you use the automatic generation method, no modification is required.

If you turn on the **Manual** switch, you must use OpenSSL or Keytool to manually generate a CRS file, and copy and paste the content of the CSR file to the **CSR File** field. For more information about how to create a CSR file, see [How do I create a CSR file?]().

**Note:**

-   Make sure that your CSR file is in the correct format. Otherwise, your certificate application may fail. We recommend that you use a CSR file that is automatically generated by SSL Certificates Service to ensure valid file content.
-   You cannot deploy certificates that use manually generated CSR files to Alibaba Cloud services.
-   You must securely store your private key when a CSR file is generated. An SSL certificate corresponds to a private key. If the private key is lost, the certificate becomes invalid. Alibaba Cloud is not responsible for storing your private key. If your private key is lost, you must re-purchase a digital certificate to replace the original one. |
|**CSR File**|This parameter must be set only after you turn on the **Manual** switch for **CSR Generation**. Enter the content of your CSR file.|

## Required application information for an EV SSL certificate

When you apply for an EV SSL certificate, you must set the parameters listed in the following table.

|Parameter|Description|
|---------|-----------|
|**Domains to Bind**|Enter the website domain name that the certificate is used to protect.Move the pointer over the ![question mark](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7541715161/p223930.png) icon to view the number and type of domain names supported, and obtain more help. The number and type of domain names supported are based on the specific configuration of the instance.

Considerations:

-   The domain name type must be the same as the value of **Type of Domain** \(Single Domain or Wildcard Domain\) that you selected when you purchase the certificate.
-   When you enter a wildcard domain name, be sure to add a wildcard character \(`*`\). An example is `*.yourwebsite.com`.
-   `.jp` domain names are not supported.
-   When you apply for a DV SSL certificate, you cannot enter `.gov` or `.edu` domain names because .gov is applicable to government agencies and .edu is applicable to educational institutions. We recommend that you purchase OV and EV SSL certificates to protect `.gov` and `.edu` domain names. |
|**Contact**|From the Contact drop-down list, select the contact \(including contact information such as the email address and mobile number\) for this certificate application.**Note:** For example, the CA may send a domain verification email to the email address specified for the contact that you select or call the specified mobile number to confirm validation. Therefore, make sure that the contact information is accurate and valid.

If you have not created a contact, click **Create Contact** to create one. SSL Certificates Service saves the created contact information for you to use next time. For more information about how to configure a new contact, see [Create a contact](/intl.en-US/Contact Management/Manage contacts.md). |
|**Company**|From the Contact drop-down list, select the company information of this certificate application, including the company name, phone number, address, and business license.If you have not created company information, click **Create Company Profile** to create company information. SSL Certificates Service saves the created company information for you to use next time. For more information about how to configure new company information, see [Create a company profile](/intl.en-US/Contact Management/Manage company profiles.md). |
|**Business License**|After a value is selected for **Company**, the uploaded business license picture in the company information is automatically selected. No modification is required.|
|**Applicant's Superior Name**|Enter the name of the superior of the applicant.|
|**Applicant's Superior Title**|Enter the job title of the superior of the applicant.|
|**Applicant's Superior Phone**|Enter the mobile number of the superior of the applicant.**Note:** Make sure that the phone number is real and valid. The CA staff will call the number to confirm certificate verification. |
|**Applicant's Superior Email Address**|Enter the email address of the superior of the applicant.**Note:** Make sure that the email address is valid and can be used to send and receive emails. Subsequent notifications such as confirmation and changes of certificate information will be sent to this email address. |
|**CSR Generation**|The Certificate Signing Request \(CSR\) file is the source file of your public key certificate and contains information about your server and organization that you must submit to the CA for review.The **Manual** switch is turned off by default, which indicates that SSL Certificates Service automatically generates a CSR file. You can download the certificate and private key after the certificate is issued. If you use the automatic generation method, no modification is required.

If you turn on the **Manual** switch, you must use OpenSSL or Keytool to manually generate a CRS file, and copy and paste the content of the CSR file to the **CSR File** field. For more information about how to create a CSR file, see [How do I create a CSR file?]().

**Note:**

-   Make sure that your CSR file is in the correct format. Otherwise, your certificate application may fail. We recommend that you use a CSR file that is automatically generated by SSL Certificates Service to ensure valid file content.
-   You cannot deploy certificates that use manually generated CSR files to Alibaba Cloud services.
-   You must securely store your private key when a CSR file is generated. An SSL certificate corresponds to a private key. If the private key is lost, the certificate becomes invalid. Alibaba Cloud is not responsible for storing your private key. If your private key is lost, you must re-purchase a digital certificate to replace the original one. |
|**CSR File**|This parameter must be set only after you turn on the **Manual** switch for **CSR Generation**. Enter the content of your CSR file.|
|**Permit for Opening a Bank Account**|You must save the scanned copy of the bank account opening license of the company in your local computer in advance, and then click **Upload File** to upload the required scanned copy from your local computer.**Note:** Make sure that the scanned copy is in PNG or JPEG format and up to 500 KB in size. |

