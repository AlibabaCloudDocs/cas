# Overview

By default, the validity period of an SSL certificate issued by a certificate authority \(CA\) is one year. To extend the validity period of your SSL certificate, you must renew the certificate within 30 calendar days before the certificate expires. SSL Certificates Service allows you to manually renew an existing certificate by purchasing a certificate with the same specifications..

## Manual renewal

To renew an existing certificate that is in the Issued or Uploaded state, you can manually **purchase a certificate** that is exactly the same as the existing certificate within **30 calendar days before the existing certificate expires**. You can purchase a certificate in the **Renewal Purchase** panel in the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas). The certificate that you manually purchased is the same as the existing certificate in terms of the **domain name type**, **certificate type**, **certificate grade**, and **certificate brand**. You can use the application information of the existing certificate to apply for certificate renewal from the CA.

After you obtain the renewed certificate, you must manually install it to your web server or Alibaba Cloud service to replace the existing certificate before the existing certificate expires.

**Automatically add the remaining validity period of the existing certificate to the validity period of the renewed certificate**

The validity period of the renewed certificate is one year from the expiration date of the existing certificate. Alibaba Cloud automatically adds the remaining validity period of the existing certificate to the validity period of the renewed certificate. Assume that the existing issued certificate is valid for one year till June 1, 2022. If you finish renewing the certificate on May 25, 2022, the expiration date of the renewed certificate is six days later than May 25, 2023. This means that the renewed certificate will expire on June 1, 2023.

**Note:** Assume that you do not purchase a certificate in the **Renewal Purchase** panel but on the buy page or that the specifications of the certificate you purchase in the **Renewal Purchase** panel are not exactly the same as those of the existing certificate. In this case, the validity period of the new certificate is one year from the time when it is issued. This validity period may overlap that of the existing certificate. The remaining validity period of the existing certificate cannot be added to the validity period of the new certificate.

**Limits**

The **Renewal Purchase** button is available only within 30 calendar days before the existing certificate that is in the Issued or Uploaded state expires.

![Renewal](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5589234161/p225624.png)

**References**

[Manual renewal](/intl.en-US/Renew Certificates/Manual renewal.md)

