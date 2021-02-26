# Manual renewal

The default validity period of an Alibaba Cloud SSL certificate that is purchased and issued by using SSL Certificates Service is one year. To continue to use your certificate after its expiration date, you must renew the certificate before it expires. Otherwise, you cannot continue to use the certificate, and your website is marked as not secure. SSL Certificates Service allows you to renew an existing paid certificate by purchasing a certificate before the existing certificate expires. The validity period of the renewed certificate is one year after the expiration date of the existing certificate.

-   The SSL certificate is in the **Pending Expiration** state.

    The **Renewal Purchase** entry is available only within 30 natural days before the certificate expires.

-   The existing certificate that you want to renew is a GlobalSign certificate.

    **Note:** Renewal is available only for GlobalSign certificates, but not for Entrust certificates.


When an SSL certificate is about to expire, [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas) generates a message to notify you that the certificate is about to expire. Within 3 to 10 business days before the certificate expires, you must purchase a certificate with the same specifications as the existing certificate on the Renewal Purchase page, and then submit a certificate renewal application. After the certificate authority \(CA\) approves your certificate renewal application, you obtain a renewed certificate. To continue to use your SSL certificate, you must install the renewed certificate on the web server to replace the existing certificate before the existing certificate expires.

After the existing certificate is renewed before expiration, Alibaba Cloud automatically adds the remaining validity period of the existing certificate to the validity period of the renewed certificate. For more information about exceptional cases, see [Limits](#section_2rn_d2i_wwh). Assume that a one-year issued certificate will expire on June 1, 2021. If you renew the certificate on May 25, 2021, the validity period of the renewed certificate is six days later than May 25, 2022. In other words, your renewed certificate will expire on June 1, 2022. Alibaba Cloud adds the remaining validity period of the existing certificate to the validity period of the renewed certificate.

**Note:** Before the existing certificate expires, you purchase a new certificate instead of renewing the existing certificate by purchasing a certificate that has the same specifications as the existing certificate. In this case, the validity period of the new certificate is one year from its issue date, and Alibaba Cloud does not add the remaining validity period of the existing certificate to the validity period of the new certificate.

A renewed certificate is issued faster than a new certificate.

## Limits

When you renew an uploaded third-party certificate by using SSL Certificates Service, Alibaba Cloud does not add the remaining validity period of the existing certificate to the validity period of the renewed certificate.

## Renewal plans

You can use different renewal plans based on whether the certificate you want to renew is issued by using SSL Certificates Service.

|Renewal plan|Scenario|Description|
|------------|--------|-----------|
|[Purchase a certificate to renew an existing Alibaba Cloud SSL certificate](#section_axb_wib_wjn)|The certificate that you want to renew is issued by using SSL Certificates Service.|When you use this plan, SSL Certificates Service automatically matches the configurations of the certificate that you want to purchase with the same specifications as the existing certificate. In addition, SSL Certificates Service automatically obtains the application information of the existing certificate, which facilitates the renewal and submission of a certificate renewal application.|
|[Renew a third-party certificate](#section_rm5_fi3_qqo)|The certificate that you want to renew is purchased from and issued by a third-party vendor and the certificate is uploaded to SSL Certificates Service for centralized management. In addition, you want to purchase and have a renewed certificate issued by using SSL Certificates Service.For more information about how to upload a certificate, see [Upload certificates](/intl.en-US/Upload Certificates/Upload certificates.md).

|Before you use this plan, obtain the specification information of the existing third-party certificate in advance.**Note:** When you renew an uploaded third-party certificate by using SSL Certificates Service, the validity period of the renewed certificate is one year from its issue date. Alibaba Cloud does not add the remaining validity period of the existing certificate to the validity period of the renewed certificate. |

## Purchase a certificate to renew an existing Alibaba Cloud SSL certificate

If the certificate that you want to renew is issued by using SSL Certificates Service, you can renew the certificate by purchasing a certificate within 30 natural days before the existing certificate expires. To do this, perform the following steps:

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  On the **Overview** page, select **Pending Expiration** from the certificate status drop-down list above the certificate list.

3.  Find the certificate that you want to renew, and click **Renewal Purchase** in the **Actions** column.

4.  Purchase a certificate to complete the renewal. The system automatically selects configurations for the certificate.

    1.  In the **Certificate Renewal** panel, click **Confirm and Renew**.

    2.  In the **Confirm and Renew** panel, click **Buy Now**, and complete the payment.

        **Note:** In the **Confirm and Renew** panel, the system automatically selects the same configurations for the certificate that you want to purchase as those of the certificate that you want to renew. You do not need to modify the configurations. If you modify the configurations, the specifications of the renewed certificate become different from those of the existing certificate. As a result, after the renewed certificate is issued, Alibaba Cloud does not add the remaining validity period of the existing certificate to the validity period of the renewed certificate.

    3.  Return to the SSL Certificates Service console. Make sure that the payment is complete. Then, close the **Confirm and Renew** panel.

    After you complete the renewal, you can view the renewed certificate below the existing certificate that is about to expire. The renewed certificate is indicated by the ![new](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5268704161/p227296.png) icon on the left side.

    At this time, the status of the renewed certificate is **Pending Verification**. SSL Certificates Service has automatically synchronized the application information and materials that you submitted last time. You must complete application verification and submit the certificate renewal application. The CA issues the renewed certificate to you only after it approves your certificate renewal application.

5.  Submit the certificate renewal application by using the renewed certificate.

    1.  Find the renewed certificate, and click **Verify** in the **Actions** column.

    2.  In the **Apply for Certificate** panel, complete the verification, and then submit the application for approval.

        For more information about how to apply for a certificate, see [Step 1: Fill in certificate application information](/intl.en-US/Issue Certificates/Apply for and validate certificates.md).

6.  Wait for the CA to approve your application and issue the renewed certificate to you.

    The issuance of DV certificates takes about 5 to 10 minutes and that of OV and EV certificates takes about 2 business days at a minimum.

7.  Install the renewed and issued certificate on your server to replace the existing certificate that is about to expire.

    **Warning:** If you do not install the renewed certificate on your server, the HTTPS service will become unavailable on your server after the existing certificate expires.

    For more information about how to install a certificate, see [How can I install SSL certificates?](/intl.en-US/Install Certificates/How can I install SSL certificates?.md).


## Renew a third-party certificate

If the certificate that you want to renew is purchased from a third-party vendor and uploaded to SSL Certificates Service, you can renew the certificate by purchasing a certificate within 30 natural days before the existing certificate expires. To do this, perform the following steps: If your certificate is not uploaded to SSL Certificates Service, upload the certificate. For more information, see [Upload certificates](/intl.en-US/Upload Certificates/Upload certificates.md).

**Note:** When you renew an uploaded third-party certificate by using SSL Certificates Service, the validity period of the renewed certificate is one year from its issue date. Alibaba Cloud does not add the remaining validity period of the existing certificate to the validity period of the renewed certificate.

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  On the **Overview** page, select **Pending Expiration** from the certificate status drop-down list above the certificate list.

3.  Find the certificate that you want to renew, and click **Renewal Purchase** in the **Actions** column.

4.  Purchase a certificate to complete the renewal. You manually select configurations for the certificate.

    1.  In the **Renewal Purchase** panel, purchase a certificate that has the same specifications as the existing certificate. The specifications include the **domain type**, **certificate type**, **certificate grade**, and **certificate brand**. Then, click **Buy Now**.

    2.  Complete the payment.

    3.  Return to the SSL Certificates Service console. Make sure that the payment is complete. Then, close the **Renewal Purchase** panel.

    After you complete the renewal, you can view the renewed certificate below the existing certificate that is about to expire. The renewed certificate is indicated by the ![new](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5268704161/p227296.png) icon on the left side.

    At this time, the status of the renewed certificate is **Pending Application**. You must submit a certificate renewal application. The CA issues the renewed certificate to you only after it approves your certificate renewal application.

5.  Submit the certificate renewal application by using the renewed certificate.

    1.  Find the renewed certificate, and click **Apply for Certificate** in the **Actions** column.

    2.  In the **Apply for Certificate** panel, enter the application information that is the same as that of the existing certificate that is about to expire. Complete the verification, and then submit the application for approval.

        For more information about how to apply for a certificate, see [Step 1: Fill in certificate application information](/intl.en-US/Issue Certificates/Apply for and validate certificates.md).

6.  Wait for the CA to approve your application and issue the renewed certificate to you.

    The issuance of DV certificates takes about 5 to 10 minutes and that of OV and EV certificates takes about 2 business days at a minimum.

7.  Install the renewed and issued certificate on your server to replace the existing certificate that is about to expire.

    **Warning:** If you do not install the renewed certificate on your server, the HTTPS service will become unavailable on your server after the existing certificate expires.

    For more information about how to install a certificate, see [How can I install SSL certificates?](/intl.en-US/Install Certificates/How can I install SSL certificates?.md).


## What to do next \(Check whether the renewed certificate takes effect\)

After the renewed certificate is installed on the server, you can visit your website by using a web browser. Then, click the ![Security lock](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5268704161/p227503.png) icon in the address bar of your browser to check whether the renewed certificate takes effect. If the validity period of the renewed certificate is displayed, the renewed certificate takes effect.

On a Linux server, you can also run the following command to view the validity period of the renewed certificate:

```
echo | openssl s_client -servername www.yourdomain.com -connect www.yourdomain.com:443 2>/dev/null | openssl x509 -noout -dates
```

