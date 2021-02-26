# Overview

The default validity period of a certificate issued by the certificate authority \(CA\) is one year. To continue to use your certificate, you must renew the certificate within 30 natural days before it expires. SSL Certificates Service allows you to manually renew an existing certificate by purchasing a certificate.

## Manual renewal

To renew an existing certificate, you can manually purchase a certificate that is exactly the same as the existing certificate within 30 natural days before the existing certificate expires. You can purchase a certificate on the **Renewal Purchase** page in the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas) console. The renewed certificate is the same as the existing certificate in terms of the domain name type, certificate type, certificate brand, and certificate grade. You can use the application information of the existing certificate to apply to the CA for certificate renewal. After the CA approves the certificate renewal application, you will obtain a newly issued certificate, which is the renewed certificate.

The validity period of the renewed certificate is one year after the expiration date of the existing certificate. This means that the remaining validity period of the existing certificate is automatically added to the validity period of the renewed certificate.

**Note:** Assume that you do not purchase a certificate on the **Renewal Purchase** page, but on the buy page, or that the certificate you purchase on the **Renewal Purchase** page is not exactly the same as the existing certificate. In this case, the validity period of the new certificate is one year from its issue date. This validity period may overlap that of the existing certificate. The remaining validity period of the existing certificate cannot be added to the validity period of the new certificate.

After you obtain the renewed certificate, you must manually install it to the web server or Alibaba Cloud service to replace the existing certificate before the existing certificate expires.

**Limits**

The **Renewal Purchase** entry is available only within 30 natural days before the existing certificate expires.

![Renewal](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5589234161/p225624.png)

**References**

For more information about how to renew an existing certificate by purchasing a certificate, see [Manual renewal](/intl.en-US/Renew Certificates/Renewal upon expiration.md).

