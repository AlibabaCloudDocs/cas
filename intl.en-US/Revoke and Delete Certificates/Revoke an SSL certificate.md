# Revoke an SSL certificate

If you no longer need to use an SSL certificate that is purchased and issued by using SSL Certificates Service or you do not want to use the SSL certificate for security reasons, you can submit a request to revoke the SSL certificate in the SSL Certificates Service console. If you revoke an SSL certificate before it expires, the SSL certificate is deregistered from the certificate authority \(CA\) that issues it. After the SSL certificate is revoked, it cannot be used for encryption and is no longer trusted by your browser.

-   The SSL certificate is purchased in the SSL Certificates Service console and is issued by the CA.

    If your certificate is a third-party certificate that is uploaded to the SSL Certificates Service console for centralized management, you cannot revoke the certificate in the SSL Certificates Service console. You must log on to the certificate system of the certificate provider to revoke the certificate.

-   The SSL certificate is valid.

You may need to revoke SSL certificates in one of the following scenarios:

-   The information that you specified to apply for an SSL certificate is not correct, but the certificate is issued. In this case, you must revoke the certificate, modify the request information, and then resubmit the request.
-   An SSL certificate is issued, but the domain names bound to the certificate need to be replaced.
-   You no longer need to use an issued SSL certificate.
-   You do not want to use an issued SSL certificate for security reasons.

If you are sure to revoke an SSL certificate, submit a revocation request in the SSL Certificates Service console before the certificate expires. After you submit a certificate revocation request, you cannot view or download the corresponding certificate in the SSL Certificates Service console.

If you want to delete an issued SSL certificate that has not expired, you must revoke it first. Then, you can delete the certificate from the certificate list in the SSL Certificates Service console. You cannot delete an SSL certificate that has not expired or has not been revoked. For more information, see [Delete an SSL certificate](/intl.en-US/Revoke and Delete Certificates/Delete an SSL certificate.md).

## Limits

Each time you purchase a certificate in the SSL Certificates Service console, you can submit one certificate revocation request. The number of revocation requests that you can use an Alibaba Cloud account to submit does not exceed the number of certificates that you have purchased by using the Alibaba Cloud account. For example, if you have purchased five certificates, you can submit five revocation requests. After you submit five revocation requests, you cannot apply to revoke certificates anymore.

If you submit a revocation request and complete the revocation process within 28 calendar days after the certificate is issued, the service quota that is used when you apply for the certificate is returned to you. If the revocation process is complete after the certificate is issued for more than 28 calendar days, the service quota that is used when you apply for the certificate is not returned to you.

## Instructions on certificate revocation and refunds

If you want to request a refund for an issued certificate, you must first apply to revoke the certificate and complete the revocation process within 28 calendar days after the certificate is issued. Otherwise, you cannot request a refund for the certificate. You cannot request a refund for a certificate that has been **issued for more than 28 calendar days** or for a certificate **that is not revoked within 28 calendar days after it is issued**. For more information about certificate refunds, see [Refund conditions](/intl.en-US/Refund/Request a refund for an SSL certificate.md).

CAs process a certificate revocation request within a maximum of five business days. If you want to revoke a certificate and request a refund, you must submit a revocation request in the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas) **at least five business days before**the 28 calendar days elapse.

**Note:** If you do not submit a revocation request in the SSL Certificates Service console at least five business days before these 28 calendar days elapse, the period after your certificate is issued may exceed 28 calendar days before the CA approves your revocation request. As a result, you cannot request a refund for your certificate.

## Procedure

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  On the **Overview** page, select **Issued** from the status drop-down list above the certificate list.

    This operation filters through all the certificates and identifies the certificates that are issued by CAs.

3.  Find the certificate that you want to revoke, click the ![More icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3285741261/p238382.png) icon in the **Actions** column, and then select **Revoke**.

4.  In the **Revoke Certificate** panel, confirm the revocation request information and click **OK**.

    ![Revoke certificates](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2226041261/p238386.png)

5.  In the **Note** message, confirm the revocation operation and click **OK** to submit the revocation request.

    ![Revocation prompt](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2226041261/p238405.png)

    **Warning:** After an issued certificate is revoked, it cannot be restored. If you submit a revocation request after the refund period elapses, you cannot request a refund after the certificate is revoked. Proceed with caution when you revoke a certificate. For more information, see [Instructions on certificate revocation and refunds](#section_9ep_pae_9j6).

    If you revoke a Domain Validation \(DV\) SSL certificate, the DV SSL certificate is revoked after you submit the revocation request. If you revoke an Organization Validation \(OV\) SSL certificate, you must perform the next step to complete the email confirmation after you submit the revocation request.

6.  If you revoke an OV SSL certificate, complete the email confirmation.

    After you submit the revocation request, the CA sends a confirmation email to your contact email address. The contact email address is the email address that you specified when you applied for the certificate. You must check the confirmation email at the email address and confirm the revocation at the earliest opportunity.

    After you complete the email confirmation, the OV SSL certificate is revoked.


## References

-   [Request a refund for an SSL certificate](/intl.en-US/Refund/Request a refund for an SSL certificate.md)
-   [Manual renewal](/intl.en-US/Renew Certificates/Manual renewal.md)

