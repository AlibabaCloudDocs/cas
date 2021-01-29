# Which domain name verification method should I choose?

According to the CA regulations, if you are applying for a free or a DV digital certificate, you must complete the domain name verification to prove your ownership of the domain name bound to the certificate. As long as the domain name authorization information is configured as required, and the domain name verification is complete, the CA detection system takes effect, the certificate can then be issued.

Alibaba Cloud SSL Certificates provides three domain name verification methods:

-   Automatic DNS verification
-   Manual DNS verification
-   File verification

**Note:** For most of the free or DV certificates, the issuing time depends on the time spent on domain name verification. If your domain name contains some sensitive words, such as bank, pay, live, the manual verification may be triggered. The manual verification may take longer time.

## Automatic DNS verification

The DNS verification method requires the domain name to be hosted on Alibaba Cloud DNS. The operating system automatically calls the Alibaba Cloud DNS API to add a record to complete domain name verification.

1.  Log on to the Alibaba Cloud [SSL Certificates console](https://yundunnext.console.aliyun.com/?spm=5176.2020520001.aliyun_sidebar.108.356a4bd3MLXFkb&p=cas#/overview/cn-hangzhou).
2.  Go to the certificate page for domain name verification and click **Apply**.
3.  On the **Apply for Certificate** page, select Automatic DNS Verification and submit the application information.
4.  On the verification information page, retrieve the **Host Name**, **Record Value**, and other domain name verification configuration information.

    **Note:** Automatic DNS verification is performed by your domain name administrator.

5.  As shown in the preceding figure, add the configuration **Value** of the certificate Verification Information page to the system by your domain name resolution service provider, such as HiChina, Xinnet, and DNSPod.

    1.  Domain names hosted on Alibaba Cloud:

        Click **Verify** on the **Apply for Certificate** page. The SSL certificates system automatically verifies the certificate for you. If the verification fails, you need to manually add DNS records in the [Alibaba Cloud DNS console](https://dns.console.aliyun.com/#/dns/domainList).

    2.  Domain names are not hosted on Alibaba Cloud:

        We recommend that you select the **Manual DNS Verification** method. If the domain name is not hosted on Alibaba Cloud DNS, you cannot use this method to complete the verification.

    **Note:** This DNS resolution record can be deleted only after the certificate has been issued or revoked.


## Manual DNS verification

If you select **Manual DNS Verification**, you must obtain the Alibaba Cloud DNS management permission and add a TXT record to your domain name resolution service provider system to complete domain name verification.

**Note:** If your domain name is not hosted on Alibaba Cloud, we recommend that you select **Manual DNS Verification**.

## File verification

File verification is typically performed by your website administrator.

1.  Log on to the Alibaba Cloud [SSL Certificates console](https://yundunnext.console.aliyun.com/?spm=5176.2020520001.aliyun_sidebar.108.356a4bd3MLXFkb&p=cas#/overview/cn-hangzhou).
2.  On the **Apply for Certificate** page, select **File Verification**.
3.  Download the **unique verification file** to your local device.
4.  Use a tool, such as FTP, to upload the **unique verification file** to the specified directory on your server .well-known/pki-validation.

    You can view the **server directory** name in the **Configuration Items** list on the **Verification Information** page.


**Note:** This verified file can be deleted only after the certificate has been issued or revoked.

**Note:** Some CAs may require you to create a hidden folder \(. xxx\). If your website server is a Windows server or uses Alibaba Cloud OSS service, you cannot create a hidden directory. We recommend that you use DNS for domain name verification instead of **File Verification**.

