# Revoke certificates

You can revoke the certificates that you no longer need or that pose security risks in the SSL Certificates Service console.

**Revoke Certificate** allows you to deregister an issued certificate from the CA. After a certificate is revoked, it is no longer valid for encryption or trustworthy for browsers. Alibaba Cloud SSL Certificates Service allows you to revoke the certificates issued by Alibaba Cloud. Third-party certificates that are uploaded to the SSL Certificates Service console cannot be revoked.

**Note:** After you submit a certificate revocation request, you cannot view or download the certificate in the SSL Certificates Service console.

You can delete revoked certificates from the SSL Certificates Service console. You cannot delete issued certificates that are not revoked. For more information about the differences between revocation and deletion, see [What is the difference between revoking a certificate and deleting a certificate?](/intl.en-US/Manage the certificates/FAQ/What is the difference between revoking a certificate and deleting a certificate?.md)

**Note:**

-   If you want to claim a refund for an issued certificate, you must request revocation for the certificate and complete the revocation process within 28 calendar days after the certificate is issued. Otherwise, the refund cannot be claimed. You cannot claim a refund for a certificate **28 calendar days after it is issued** or for a certificate **that is not revoked within 28 calendar days after it is issued**.
-   Certificate authorities \(CAs\) can process a certificate revocation request within a maximum of 5 business days. If you want to revoke a certificate and claim a refund, you must submit the certificate revocation request in the Alibaba Cloud SSL Certificates console 28 calendar days the 28 calendar days elapse. Otherwise, the revocation request may fail to be approved in time, and the refund request will be rejected.

## Procedure

1.  On the Overview page, find the certificate that you want to revoke and click **Revoke**.

    ![Revoke](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8700955951/p39609.png)

2.  In the Revoke Certificate panel, specify Revocation Cause and click **OK**.

3.  In the message that appears, click **OK**.

4.  Complete the email confirmation.

    After you submit the revocation request, the CA sends a confirmation email to the address that you specified for **Applicant's Email Address**. You must check for the email and confirm the revocation activity promptly.

    **Note:** CAs send confirmation emails only for OV and EV certificates. If you want to revoke DV certificates, the CAs do not send confirmation emails.

    After you complete the email confirmation, the certificate is revoked.


## References

[Refund instructions](/intl.en-US/Product pricing/Refund instructions.md)

[Renewal upon expiration](/intl.en-US/Product pricing/Renewal upon expiration.md)

