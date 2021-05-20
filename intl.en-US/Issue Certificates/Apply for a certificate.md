# Apply for a certificate

After you purchase an SSL Certificates Service instance, you must use the instance to submit a certificate request to the certificate authority \(CA\). After the CA approves your request, the CA issues the certificate to you. Then, you can install the issued certificate on your server to enable HTTPS for your website.

An SSL Certificates Service instance is purchased.

For more information, see [Purchase an SSL Certificates Service instance](/intl.en-US/Buy Certificates/Purchase an SSL Certificates Service instance.md).

## Procedure

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  On the **Overview** page, select **Pending Application** from the status drop-down list above the certificate list.

    This operation filters through all the purchased certificate instances and identifies the instances that you have not used to submit certificate applications.

3.  Find the SSL Certificates Service instance that you want to use and click **Apply for Certificate** in the **Actions** column.

4.  In the **Apply for Certificate** panel, set the parameters to apply for a certificate.

    The parameters vary with certificate type. Set the parameters by following the instructions in the Apply for Certificate panel.

    For more information about the parameters, see [Required information for certificate application](/intl.en-US/Issue Certificates/Required information for certificate application.md).

5.  Submit the request to the CA for review.

    After you enter all the request information, perform the following operations based on the type of the certificate for which you want to apply:

    -   Domain Validation \(DV\) SSL certificate: Click **Next**, complete the domain ownership verification based on the instructions, and then click **Submit**.

        For more information about the domain ownership verification, see [How do I configure domain name authorization?](/intl.en-US/Issue Certificates/FAQ/How do I configure domain name authorization?.md).

    -   Organization Validation \(OV\) or Extended Validation \(EV\) SSL certificate: Click **Submit**.
    After you submit the certificate request, the message that prompts subsequent operations appears. Make sure that the phone calls from the CA are properly answered and check the verification email at the earliest opportunity as prompted. The CA sends the verification email to your contact email address.

    ![Prompt to submit for review](../images/p211277.png)


## What to do next

-   Before certificate issuance

    **Note:** If you want to modify the information in your request before your certificate is issued, you can withdraw the certificate request. Then, modify the information and resubmit the request. You cannot withdraw the certificate request after the certificate is issued.

    |Certificate type|What to do next|
    |----------------|---------------|
    |DV SSL certificates|Wait for the CA to review your certificate request. After the CA approves the request, the CA issues the certificate to you. In normal cases, DV SSL certificates are reviewed and issued within 2 hours. You can view the status of the certificate in the certificate list. After the certificate is issued, the value of **Status** of the certificate changes to **Issued**. |
    |OV and EV SSL certificates|After the CA receives your certificate request, the CA verifies your certificate qualification. The CA issues a certificate to you only after the verification is passed. The requirements and the time required for verification vary based on CAs. In normal cases, OV and EV SSL certificates are reviewed and issued within three to five business days. After you submit the certificate request, you must cooperate with the CA reviewer to complete the following verification:

    -   Domain name verification: After the CA receives your certificate application, the CA sends an email for domain name verification to your contact email address. You must perform the following steps to verify the domain name.

![Verification process](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9115585751/p6087.jpg)

**Note:** If the domain name is not verified, your request cannot be approved and the certificate status remains **Validating Application**.

    -   Phone verification: The CA staff may call your contact phone number to verify your certificate request information, based on the requirements of the CA. Make sure that the phone calls from the CA are properly answered.
After the verification is passed, you can view the status of the certificate in the certificate list. After the certificate is issued, the value of **Status** of the certificate changes to **Issued**.

If the verification fails, you can view the failure cause in the Status column. You must modify the request information, especially the enterprise qualification information, based on the failure cause, and then resubmit the certificate request for review. |

-   After certificate issuance

    Install the issued SSL certificate to your web server or deploy it to the Alibaba Cloud service that needs to use the certificate.

    For more information, see [How can I install SSL certificates?](/intl.en-US/Install Certificates/How can I install SSL certificates?.md) and [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md).


