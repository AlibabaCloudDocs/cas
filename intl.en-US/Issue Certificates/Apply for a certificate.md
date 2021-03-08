# Apply for a certificate

If you have purchased a one-year certificate instance, you must apply for a certificate to the certificate authority \(CA\) by using SSL Certificates Service. After your certificate application is approved by the CA, the CA issues the certificate to you. Then, you can install the issued certificate on your server to use HTTPS for your website.

A one-year certificate instance is purchased in the SSL Certificates Service console.

For more information, see [Select and purchase certificates](/intl.en-US/Buy Certificates/Select and purchase certificates.md).

## Use a one-year certificate instance to apply for a certificate

After you purchase an **SSL Certificates Service \(One Year\)** certificate instance, you can perform the following steps to apply for a certificate to the CA:

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  On the **Overview** page, select **Pending Application** from the status drop-down list above the certificate list.

    This operation filters through all the purchased certificate instances and identifies the instances for which you have not submitted applications.

3.  Find the certificate instance that you want to use, and click **Apply for Certificate** in the **Actions** column.

4.  In the **Apply for Certificate** panel, set the required parameters.

    The application information varies based on certificate types.Enter the information as prompted.

    For more information about the parameters, see [Required information for certificate application](/intl.en-US/Issue Certificates/Required information for certificate application.md).

5.  Submit the certificate application to the CA for review.

    After you enter all the application information, perform the following steps based on the certificate type for which you want to apply:

    -   Domain Validation \(DV\) SSL certificate: Click **Next**, complete the verification of domain name ownership as prompted, and then click **Submit**.

        For more information about the verification of domain name ownership, see [How do I configure domain name authorization?](/intl.en-US/Issue Certificates/FAQ/How do I configure domain name authorization?.md).

    -   Organization Validation \(OV\) or Extended Validation \(EV\) SSL certificate: Click **Submit**.
    After you submit the certificate application, you will receive the following note. Keep the phone number of the contact reachable and check the verification email at the earliest opportunity as prompted. The CA sends the verification email to the email address of the contact.

    ![Prompt to submit for review](../images/p211277.png)


## What to do next

-   Before certificate issuance

    **Note:** Before your certificate is issued, if you want to modify its application information, you can withdraw the application and resubmit the application after you modify the information. You cannot withdraw the application after the certificate is issued.

    |Certificate types|What to do next|
    |-----------------|---------------|
    |DV SSL certificates|Wait for the CA to review your certificate application. The CA issues the certificate to you after your application is approved. DV SSL certificates are typically reviewed and issued within 2 hours.You can view the status of the certificate in the certificate list. After the certificate is issued, the value of **Status** of the certificate is updated to **Issued**. |
    |OV and EV SSL certificates|After the CA receives your certificate application, the CA verifies your certificate qualification. The CA issues a certificate to you only after the verification is passed. The requirements and the time required for verification vary based on CAs. OV and EV SSL certificates are typically reviewed and issued within three to five business days.After you submit the certificate application, you must cooperate with the CA reviewer to complete the following verification:

    -   Domain name verification: After the CA receives your certificate application, the CA sends an email for domain name verification to the email address of your contact. You must perform the following steps to verify the domain name.

![Verification process](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9115585751/p6087.jpg)

**Note:** If domain name verification is not complete, certificate review fails and the certificate status remains **Validating Application**.

    -   Phone verification: Based on requirements of the CA, the CA staff may call the phone number of your contact to verify your certificate application information. Keep the phone number of the contact reachable to answer the verification call from the CA.
After the verification is passed, you can view the status of the certificate in the certificate list. After the certificate is issued, the value of **Status** of the certificate is updated to **Issued**.

If the verification fails, you can view the failure cause in the Status column. You must modify the application information, especially the enterprise qualification information, based on the failure cause, and then resubmit the certificate application for review. |

-   After certificate issuance

    Install the issued SSL certificate to your web server or deploy it to the Alibaba Cloud service that needs to use the certificate.

    For more information, see [How can I install SSL certificates?](/intl.en-US/Install Certificates/How can I install SSL certificates?.md) and [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy certificates on Alibaba Cloud services.md).


