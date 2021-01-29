# Guidelines for OSS users applying for SSL certificates

This topic provides guidelines for Alibaba Cloud OSS users to apply for SSL certificates.

You can manage your SSL certificates in the OSS console as follows:

1.  Apply for a new SSL certificate.
2.  Upload an existing SSL certificate for management.

Procedure: choose **Bucket** \> **Domain Name** \> **Certificates Service**.

## Paid version of EntrustOV or EntrustEV SSL certificates

Your domain name must be hosted on Alibaba Cloud so that Alibaba Cloud can automatically issue the certificate that you have applied for.

If the DNS record is not hosted on Alibaba Cloud, the certificate you applied for cannot be automatically issued. You must check the certificate **Status** in SSL Certificates console and configure the DNS record as instructed.

**Note:**

If you are not authorized to configure DNS records, we recommend you authorize Alibaba Cloud to configure the DNS record for you. If you are authorized to configure DNS records, purchase a DV SSL certificate in the [Alibaba Cloud SSL Certificates console](https://account.alibabacloud.com/login/login.htm). After you purchase the certificate, follow the DNS verification requirements shown in the console to configure a TXT DNS record on the third-party DNS resolution platform. This demonstrates your ownership to the domain name, so that your SSL certificate can be issued.

If a large number of SSL certificates need to be issued, we recommend that you authorize Alibaba Cloud to configure the DNS record for you. This simplifies the procedure of certificate application and management.

