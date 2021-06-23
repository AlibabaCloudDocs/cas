# Apply for a certificate

After you purchase an SSL certificate instance, you must submit a certificate application to a certificate authority \(CA\) by using SSL Certificates Service. After the CA approves your certificate application, the CA issues the certificate to you. Then, you can install the issued certificate on your web server to enable HTTPS for your website.

An SSL certificate instance is purchased.

For more information, see [Purchase an SSL Certificates Service instance](/intl.en-US/Buy Certificates/Purchase an SSL Certificates Service instance.md).

## Procedure

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  On the **Overview** page, select **Pending Application** from the status drop-down list above the certificate list.

    This operation filters through all the purchased certificate instances and identifies the instances that you have not used to submit certificate applications.

3.  Find the certificate instance that you want to use and click **Apply for Certificate** in the **Actions** column.

4.  In the **Apply for Certificate** panel, configure the parameters.

    The parameters vary based on certificate types. You need to configure the parameters as prompted.

    For more information about the parameters, see [Required information for certificate application](/intl.en-US/Issue Certificates/Required information for certificate application.md).

5.  Submit the certificate application to the CA for review.

    After you configure the parameters, perform the following operations based on the type of the certificate that you want to apply for:

    -   Domain Validation \(DV\) SSL certificate: Click **Next**, verify domain name ownership as prompted, and then click **Submit**.

        For more information about how to verify domain name ownership, see [How do I verify domain name ownership?](/intl.en-US/Issue Certificates/FAQ/How do I configure domain name authorization?.md)

    -   Organization Validation \(OV\) or Extended Validation \(EV\) SSL certificate: Click **Submit**.
    After you submit the certificate application, the following message appears. Make sure that the phone calls from the CA are properly answered and check the verification email at the earliest opportunity as prompted. The CA sends the verification email to your contact email address.

    ![Message that notifies you of submitting an application review](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5357023261/p211277.png)


## What to do next

-   Before certificate issuance

    **Note:** If you want to modify your certificate application before the certificate is issued, cancel the application, modify the application, and then submit the modified application. If the certificate is issued, you cannot cancel the certificate application.

    |Certificate type|What to do next|
    |----------------|---------------|
    |DV SSL certificate|Wait for the CA to review your certificate application. After the CA approves the application, the CA issues the certificate to you. In most cases, DV SSL certificates are reviewed and issued within 2 hours. You can view the status of the certificate in the certificate list. After the certificate is issued, the value of **Status** changes to **Issued**. |
    |OV or EV SSL certificate|After the CA receives your certificate application, the CA verifies the information in your application. The CA issues a certificate to you only after the certificate passes the verification. The requirements and the time required for verification vary based on CAs. In most cases, OV or EV SSL certificates are reviewed and issued within 3 to 5 business days. After you submit the certificate application, you must cooperate with the CA staff to complete the following verification process:

    -   Domain name verification: After the CA receives your certificate application, the CA sends an email for domain name verification to your contact email address. To verify the domain name, perform the following operations:

![Verification process](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9115585751/p6087.jpg)

**Note:** If the domain name fails verification, your application will not be approved, and the certificate remains in the **Validating Application** state.

    -   Verification by phone: The CA staff may contact you by phone to verify the information in your application. Make sure that the phone calls from the CA are properly answered.
After the certificate passes the verification, you can view the status of the certificate in the certificate list. After the certificate is issued, the value of **Status** changes to **Issued**.

If the certificate application fails, you can view the failure cause in the Status column. You must modify the information in the application, especially the enterprise qualification information, based on the failure cause. Then, submit the application again. |

-   After certificate issuance

    Install the issued SSL certificate on your web server or deploy the certificate to an Alibaba Cloud service that requires the certificate. For more information, see [Installation overview](/intl.en-US/Install Certificates/Installation overview.md).


