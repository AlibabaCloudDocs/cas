# Revoke certificates

You can apply to revoke a certificate in the SSL Certificate console for security purposes, or when you no longer need it.

**Revoke Certificate** allows you to deregister an issued certificate from the CA. After a certificate is revoked, it is no longer valid for encryption or trustworthy for browsers. Alibaba Cloud SSL Certificates Service allows you to revoke certificates issued by Alibaba Cloud. Uploaded third-party certificates cannot be revoked.

**Note:** After a certificate revocation application is submitted, you cannot view or download the certificate in the SSL Certificate console.

You can only delete revoked SSL certificates in the SSL Certificate console, but cannot delete issued SSL certificates which are not revoked. For the differences between revocation and deletion, see [What is the difference between revoking a certificate and deleting a certificate?](/intl.en-US/Manage the certificates/FAQ/What is the difference between revoking a certificate and deleting a certificate?.md)

**Note:**

-   If you require refunds for issued certificates, you must revoke the certificates within 30 calendar days after the certificates have been issued. Otherwise, refunds cannot be issued. No refund will be issued for a certificate that is **issued over 30 calendar days** or whose **revocation process cannot be completed within 30 calendar days after the issuance of the certificate**.
-   It takes up to five business days for the certification authority \(CA\) to process a certificate revocation application. If you need to revoke a certificate and apply for a refund, apply for the revocation in the Alibaba Cloud SSL Certificate console **at least five business days in advance**, within 30 calendar days after the certificate is issued. If you do not reserve enough revocation processing time, your certificate may be in effect more than 30 calendar days after it was issued and a refund cannot be made.

## Procedure

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  In the left-side navigation pane, click **Overview**.

3.  On the SSL Certificates page, find the certificate to be revoked in the Signed certificate list, and click **revoke**.

    ![Revoke](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8700955951/p39609.png)

4.  On the Revoke Certificate page, select the revocation cause and click **Confirm**.

5.  In the dialog box that appears, click **OK**.

6.  Complete the email confirmation.

    After you submit an application for certificate revocation, the CA will send you a confirmation email to the **Applicant's Email Address**. Check the email in time and confirm the revocation of certificates.

    **Note:** After you submit an application for certificate revocation, you will receive a confirmation email for OV and EV certificates sent from the CA. An application for DV certificate revocation does not require email confirmation.

    After you complete the email confirmation, the certificate is revoked successfully.


## References

[Refund instructions](/intl.en-US/Product pricing/Refund instructions.md)

[Renewal upon expiration](/intl.en-US/Product pricing/Renewal upon expiration.md)

