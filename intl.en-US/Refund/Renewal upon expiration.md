# Renewal upon expiration

You must renew your SSL certificate before it expires. Otherwise, you cannot continue to use the SSL certificate, which may cause your website to be marked as not secure. Alibaba Cloud SSL Certificates Service allows you to renew your certificate upon expiration. For early renewals, the remaining validity of your certificate will be added to the validity period of the renewed certificate.

You have purchased a GlobalSign certificate.

**Note:** Renewal is supported only for GlobalSign certificates, but not for Entrust certificates.

Post-payment is not accepted. You must pay first to use an SSL certificate.

The SSL Certificates Service console will notify you of upcoming expiration 60 days in advance. You must renew your certificate 3 to 10 business days before it expires to ensure that the certificate renewal can be approved before your certificate expires.

If you renew your certificate before it expires, Alibaba Cloud automatically adds the remaining validity of the old certificate to the validity period of the renewed certificate. However, this rule does not apply to free Domain Validation \(DV\) certificates and DigicertDV wildcard certificates.

For example, an issued certificate with one-year validity will expire on May 1, 2021. If you renew the certificate on April 25, 2021, the renewed certificate will be valid for one year plus six days starting from April 25, 2021. This means that your renewed certificate will expire on May 1, 2022. Alibaba Cloud has added the remaining validity of your old certificate to the validity period of the renewed certificate.

**Note:** If your existing certificate is about to expire and you purchase a new certificate instead of renewing the existing certificate upon expiration, the remaining validity of the existing certificate cannot be added to the validity period of your newly purchased certificate.

A renewed certificate is issued faster than a newly purchased certificate.

## Limits

Make sure that the certificate you want to renew is a GlobalSign certificate.

**Note:** Renewal is supported only for GlobalSign certificates, but not for Entrust certificates.

The renewed certificate must be consistent with the existing certificate in terms of certificate type, certification authority \(CA\), and applicant information. Otherwise, the renewed certificate will be identified as a newly purchased certificate, and the remaining validity of your existing certificate will not be counted.

## Step 1: View certificates that are about to expire

1.  View **Will Expire** certificates.

2.  View the notes about certificate renewal before you renew a certificate.

    In the certificate list of the Pending Expiration section, move the pointer over ![Notes](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7782027951/p66668.png) in the **Expire On** column to view the renewal notes.

    -   After you renew a certificate, log on to the SSL Certificates Service console and apply for certificate renewal as instructed.
    -   The console stores your previous application information. Therefore, you do not need to enter the information again during the application.
    -   Wait for the CA to approve your application. After the renewal is completed, you will obtain a renewed certificate.
    -   After the renewed certificate is issued, replace your expiring certificate with the renewed certificate.
    Alternatively, click **Renew Now** above the certificate list to obtain the certificate renewal procedure.


## Step 2: Renew a certificate

1.  In the certificate list of the **Pending Expiration** section, find the target certificate and click **Renewal** in the **Expire On** column.

    ![Renewal](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8782027951/p101927.png)

2.  On the certificate buy page, select the type and configuration of your certificate.

    **Note:**

    -   After the renewal is completed, you will receive a new certificate order. You must apply for the certificate, so that the CA can issue it.
    -   The brand and type of the certificate after renewal are the same as those of the certificate that you purchase.
3.  Click **Buy Now**.

4.  Select **I agree to the Alibaba Cloud certificates service \(subscription\) agreement of service**, and click **Pay** to complete the renewal.

5.  Log on to the SSL Certificates Service console. In the **Confirm that the renewal has been completed?** dialog box, click **OK**.

6.  In the certificate list of the **Pending Expiration** section, find the certificate that has been renewed and click **Certificate Application** in the **Actions** column to submit the information for verification.

    For more information, see [Step 1: Fill in certificate application information](/intl.en-US/Issue Certificates/Application process/Apply for and validate certificates.md).

    **Note:** When you apply for a certificate, Alibaba Cloud SSL Certificates Service automatically synchronizes the application information and data that you submitted last time.

7.  Click **Submit**.

8.  Wait for the CA to approve and issue the certificate.

    The issuance of a DV certificate takes about 5 to 10 minutes, and the issuance of an OV or EV certificate takes at least two business days.

9.  Install the renewed certificate on your server to replace the certificate that is about to expire.

    **Note:** If you do not install the renewed certificate on your server, the HTTPS service will become unavailable after the existing certificate expires.


## Step 3: Check whether the certificate has been updated

After you install the renewed certificate on your server, click the security lock in the address bar of your browser to check whether the certificate validity period has been updated. If a new validity period is displayed, your certificate has been updated.

-   View the validity period of the renewed certificate on a Linux server

    ```
    echo | openssl s_client -servername www.yourwebsite.com -connect www.yourwebsite.com:443 2>/dev/null | openssl x509 -noout -dates
    ```

-   View the validity period of the renewed certificate on a Windows server

## References

-   [Install SSL certificates on Tomcat servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md)
-   [Install SSL certificates on Apache servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates on Apache servers.md)
-   [Deploy SSL certificate on Ubuntu Apache2](/intl.en-US/Best Practices/Deploy SSL certificate on Ubuntu Apache2.md)
-   [How do I deploy the issued certificate in Apache server]()
-   [Install an SSL certificate on an NGINX or Tengine server](/intl.en-US/Install Certificates/Install certificates to servers/Install an SSL certificate on an NGINX or Tengine server.md)
-   [Install SSL certificates in IIS servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates in IIS servers.md)
-   [Deploy SSL certificates on CentOS-based Tomcat 8.5 or 9.0](/intl.en-US/Best Practices/Deploy SSL certificates on CentOS-based Tomcat 8.5 or 9.0.md)
-   [An SSL certificate is configured by the jetty server](/intl.en-US/Install Certificates/Install certificates to servers/An SSL certificate is configured by the jetty server.md)

