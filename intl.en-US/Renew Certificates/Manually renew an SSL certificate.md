# Manually renew an SSL certificate

Every SSL certificate has a validity period. You must renew an SSL certificate before it expires. Otherwise, the certificate will not be trusted after it expires. This brings security risks to the website that the certificate protects. Users of the website are warned that the website is not secure, or cannot visit the website. This topic describes how to renew an SSL certificate that is about to expire in the SSL Certificates Service console.

For more information about how to renew SSL certificates, see [Manual renewal](/intl.en-US/Renew Certificates/Overview.md).

## Prerequisites

-   A paid Alibaba Cloud SSL certificate you applied for in the SSL Certificates Service console is used, or a third-party SSL certificate uploaded to the SSL Certificates Service console for centralized management is used.
-   Your SSL certificate is in the **Pending Expiration** state.

    The **Renewal Purchase** button is available only within 30 calendar days before the certificate expires.

-   The existing SSL certificate that you want to renew is issued by GlobalSign.

    You can renew only SSL certificates issued by GlobalSign.


## Notes on unavailability of the remaining validity period of the existing certificate for third-party certificates

If you renew an uploaded third-party certificate by using SSL Certificates Service, Alibaba Cloud does not add the remaining validity period of the existing certificate to the validity period of the renewed certificate.

## Renew an Alibaba Cloud SSL certificate

If your certificate is purchased and issued by using SSL Certificates Service, you can manually renew the certificate when the certificate is **about to expire**. To manually renew your certificate, perform the following operations:

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  On the **Overview** page, select **Pending Expiration** from the certificate status drop-down list above the certificate list.

    This operation shows you all the certificates that meet the renewal conditions.

    If the certificate list is empty after you perform this operation, you do not have a certificate in the **Pending Expiration** state. Therefore, you do not need to renew a certificate.

3.  Find the certificate that you want to renew, and click **Renewal Purchase** in the **Actions** column.

4.  Complete the purchase as prompted.

    In the **Buy Now** panel, the system automatically selects the same configurations for the certificate you want to purchase as those of the certificate you want to renew. You do not need to modify the configurations. If you modify the configurations, the specifications of the certificate purchased for renewal become different from those of the existing certificate. After the certificate purchased for renewal is issued, Alibaba Cloud does not add the remaining validity period of the existing certificate to the validity period of the renewed certificate.

    Perform the following operations:

    1.  In the **Buy Now** panel, click **Buy Now**.

    2.  Confirm the order and complete the payment.

    3.  Return to the SSL Certificates Service console and confirm that the payment is complete.

    After you complete the purchase, the renewed certificate appears below your existing certificate that is about to expire. The ![new](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5268704161/p227296.png) icon appears on the left of the renewed certificate. The icon indicates that the renewed certificate is associated with the existing certificate.

    At this time, the status of the renewed certificate is **Pending Application**. You must submit a certificate application. The CA issues the renewed certificate to you only after it approves your certificate application.

5.  Submit a certificate application.

    For more information about how to apply for a certificate, see [Apply for a certificate](/intl.en-US/Issue Certificates/Apply for a certificate.md).

6.  Wait for the CA to approve your application and issue the renewed certificate to you.

    Domain Validation \(DV\) SSL certificates can be issued within a minimum of 5 to 10 minutes. Organization Validation \(OV\) SSL certificates and Extended Validation \(EV\) SSL certificates can be issued within a minimum of two business days.

7.  Install the issued renewed certificate on your server to replace the existing certificate that is about to expire.

    **Warning:** If you do not install the renewed certificate on your server, the HTTPS service will become unavailable on your server after the existing certificate expires.

    For more information about how to install an SSL certificate, see [How can I install SSL certificates?](/intl.en-US/Install Certificates/How can I install SSL certificates?.md).


## Renew an uploaded third-party SSL certificate

If your certificate is purchased and issued by using a third-party platform and is uploaded to the SSL Certificates Service console for centralized management, you can manually renew the certificate when it is **about to expire**. For more information about how to upload an SSL certificate, see [Upload certificates](/intl.en-US/Upload Certificates/Upload certificates.md).

**Note:** When you renew an uploaded third-party certificate by using SSL Certificates Service, the validity period of the renewed certificate is one year from the time when it is issued. Alibaba Cloud does not add the remaining validity period of the existing certificate to the validity period of the renewed certificate.

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  On the **Overview** page, select **Pending Expiration** from the certificate status drop-down list above the certificate list.

    This operation shows you all the certificates that meet the renewal conditions.

    If the certificate list is empty after you perform this operation, you do not have a certificate in the **Pending Expiration** state. Therefore, you do not need to renew a certificate.

3.  Find the **uploaded certificate** that you want to renew and click **Renewal Purchase** in the **Actions** column.

4.  Complete the purchase as prompted.

    1.  In the **Renewal Purchase** panel, purchase a certificate that has the same specifications as the existing certificate. The specifications include the **domain name type**, **certificate type**, **certificate grade**, and **certificate brand**. Then, click **Buy Now**.

    2.  Confirm the order and complete the payment.

    3.  Return to the SSL Certificates Service console and confirm that the payment is complete.

    After you complete the purchase, the renewed certificate appears below your existing certificate that is about to expire. The ![new](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5268704161/p227296.png) icon appears on the left of the renewed certificate. The icon indicates that the renewed certificate is associated with the existing certificate.

    At this time, the status of the renewed certificate is **Pending Application**. You must submit a certificate application. The CA issues the renewed certificate to you only after it approves your certificate application.

5.  Submit a certificate application.

    For more information about how to apply for a certificate, see [Apply for a certificate](/intl.en-US/Issue Certificates/Apply for a certificate.md).

6.  Wait for the CA to approve your application and issue the renewed certificate to you.

    Domain Validation \(DV\) SSL certificates can be issued within a minimum of 5 to 10 minutes. Organization Validation \(OV\) SSL certificates and Extended Validation \(EV\) SSL certificates can be issued within a minimum of two business days.

7.  Install the issued renewed certificate on your server to replace the existing certificate that is about to expire.

    **Warning:** If you do not install the renewed certificate on your server, the HTTPS service will become unavailable on your server after the existing certificate expires.

    For more information about how to install an SSL certificate, see [How can I install SSL certificates?](/intl.en-US/Install Certificates/How can I install SSL certificates?.md).


## What to do next \(Check whether the renewed certificate takes effect\)

After the renewed certificate is installed on your web server, you can visit your website by using a web browser. Then, click the ![Security lock](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5268704161/p227503.png) icon in the address bar of your browser to check whether the renewed certificate takes effect. If the validity period of the renewed certificate appears, the renewed certificate takes effect.

On a Linux server, you can also run the following command to view the validity period of the renewed certificate:

```
echo | openssl s_client -servername www.yourdomain.com -connect www.yourdomain.com:443 2>/dev/null | openssl x509 -noout -dates
```

