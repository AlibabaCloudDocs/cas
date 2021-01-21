# \[Important\] GlobalSign upgraded the intermediate root certificate of DV SSL certificates

On January 21, 2021, GlobalSign upgraded the intermediate root certificate of DV SSL certificates. Take note of the following notice:

Dear customers,

To comply with the Certificate Authority Browser Forum security specifications and requirements for SSL certificates, GlobalSign has upgraded the intermediate root certificate of DV SSL. The old intermediate certificate \(model: **GlobalSign RSA DV SSL CA 2018**\) has been replaced with a new intermediate certificate \(model: **GlobalSign GCC R3 DV TLS CA 2020**\). This upgrade improves the security performance of DV SSL certificates.

We recommend that our customers use new public and private keys to reissue DV SSL certificates and redeploy the certificate. Once reissued, you will get a DV SSL certificate with the latest intermediate certificate.

Thank you for your support. We wish you a Happy New Year in advance.

GlobalSign APAC

## Alibaba Cloud solution

After GlobalSign upgraded the intermediate root certificate of DV SSL certificates, all the GlobalSign DV SSL certificates that were issued by using Alibaba Cloud SSL Certificates Service before 00:00:00 \(UTC+8\) on January 21, 2021 are revoked. GlobalSign plans to re-issue all the affected certificates by January 22, 2021. Alibaba Cloud will use newly issued certificates to overwrite affected certificates.

If you use a GlobalSign DV SSL certificate, you must go to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas) to download the newly issued certificate. Then, re-deploy the certificate to your server to replace your original certificate. Otherwise, HTTPS access to your website fails.

If you encounter any issues during deployment, contact us for one-on-one technical support.

## Alibaba Cloud compensation

If your certificates are revoked due to this upgrade, you will receive 50% off the list price the next time you renew your GlobalSign DV SSL certificates.

