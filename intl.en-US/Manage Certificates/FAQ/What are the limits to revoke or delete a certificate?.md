# What are the limits to revoke or delete a certificate?

Alibaba Cloud SSL Certificates Service allows you to revoke issued certificates and delete expired or revoked certificates. If you revoke a certificate, it is deregistered from the certificate authority \(CA\). After a certificate is revoked, it can no longer be used for encryption or used to verify trusted websites. If you delete a certificate, its resources are deleted from Alibaba Cloud SSL Certificates Service.

## When do I need to revoke a certificate? What are the limits to revoke a certificate?

You may need to revoke a certificate in the following scenarios:

-   The information that you specified to apply for a certificate is not correct, but the certificate is issued. In this case, you must revoke the certificate before you can resubmit the application with the correct information.
-   A certificate is issued, but the domain names bound to the certificate need to be replaced.
-   You no longer need a certificate.
-   For security reasons, a certificate is no longer used.

No limits are imposed to revoke a certificate. You can place a revocation request at all times. For more information, see [Revoke certificates](/intl.en-US/Manage Certificates/Revoke certificates.md).

If you complete the revocation process for a paid certificate within 30 days after the certificate is issued, you can claim a full refund for the certificate. If you complete the process after 30 days, you cannot claim a refund for the certificate. The certification revocation process is considered complete only after the revocation request is submitted and approved.

**Note:** A revoked certificate can no longer be used for encryption. Proceed with caution.

## What are the limits to delete a certificate?

Take not of the following limits:

-   If a certificate does not expire, you cannot delete it until it is revoked.
-   If a certificate expires, you can delete it at all times.
-   If a certificate is manually deleted, you cannot delete it until it expires.

