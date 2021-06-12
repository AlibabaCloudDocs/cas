# Deploy certificates to Alibaba Cloud services

SSL Certificates Service allows you to deploy issued certificates and uploaded third-party certificates to supported Alibaba Cloud services with a few clicks.

-   The following Alibaba Cloud services are activated: **WAF**, **OSS**, **CLB**, **ALB**, **Alibaba Cloud CDN**, **Secure CDN**, **Dynamic Route for CDN**, **ApsaraVideo Live**, and **Anti-DDoS**. Domain names that match the certificates to be deployed are configured for the Alibaba Cloud services.

    For more information about the introduction and usage of the Alibaba Cloud services, see [Supported Alibaba Cloud services](/intl.en-US/Product Introduction/What is SSL Certificates Service?.md).

-   The certificates that you want to deploy are issued by using SSL Certificates Service, or the third-party certificates that you want to deploy are uploaded to SSL Certificates Service.

    For more information, see [Apply for a certificate](/intl.en-US/Issue Certificates/Apply for a certificate.md) and [Upload certificates](/intl.en-US/Upload Certificates/Upload certificates.md).


## Limits on certificate deployment on a CLB instance or an ALB instance

When you deploy a certificate to a **Classic Load Balancer \(CLB\)** instance or an **Application Load Balancer \(ALB\)** instance by using SSL Certificates Service, take note of the following limits. CLB is formerly known as Server Load Balancer \(SLB\).

-   If HTTPS listeners that have mutual authentication enabled are added to the CLB or ALB instance, you cannot deploy a certificate to the CLB or ALB instance by using SSL Certificates Service.

    In this case, you can deploy the required certificate only in the [SLB console](https://slb.console.aliyun.com/slb/overview). For more information, see [Configure an HTTPS listener \(mutual authentication\)](/intl.en-US/Tutorials/CLB/Configure an HTTPS listener (mutual authentication).md).

-   If a certificate is deployed to a CLB instance or an ALB instance and you want to replace this certificate with a new certificate, the domain name that is bound to the new certificate must be the same as or contain the domain name bound to the existing certificate. Examples:

    -   You have deployed a certificate to which the single domain name `example.com` is bound to the CLB or ALB instance. If you want to replace this certificate with a new certificate by using SSL Certificates Service, the domain name that is bound to the new certificate must be the same as or contain the domain name `example.com`. For example, the domain name that is bound to the new certificate can be `example.com`, `www.example.com`, or `*.example.com`.
    -   You have deployed a certificate to which the wildcard domain name `*.example.com` is bound to the CLB or ALB instance. If you want to replace this certificate with a new certificate by using SSL Certificates Service, the domain name that is bound to the new certificate must be the same as or contain the domain name `*.example.com`. For example. the domain name that is bound to the new certificate can be `*.example.com` or `example.com`.
    If you want to replace an existing certificate on the CLB or ALB instance with a new certificate that does not meet the requirements, you can deploy the new certificate only in the [SLB console](https://slb.console.aliyun.com/slb/overview). For more information, see [Add an HTTPS listener to a CLB instance](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Add an HTTPS listener.md).


## Procedure

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  On the Overview page, select **Issued** from the status drop-down list above the certificate list.

    When you select Issued, all the certificates that are issued by certificate authorities \(CAs\) are displayed.

3.  Find the certificate that you want to deploy and click **Deploy** in the **Actions** column.

4.  In the **Deploy Certificate** panel, select an Alibaba Cloud service to which you want to deploy the certificate from the **Select Cloud Service** drop-down list. For example, if you want to deploy the certificate to a domain name that is added to Web Application Firewall \(WAF\), select **WAF**.

    The valid values of Select Cloud Service are **WAF**, **OSS**, **CLB**, **ALB**, **Alibaba Cloud CDN**, **Secure CDN**, **Dynamic Route for CDN**, **ApsaraVideo Live**, and **Anti-DDoS**

    ![Supported Alibaba Cloud services](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5891085161/p111871.png)

    After you select an Alibaba Cloud service, the domain name list in the lower part of the page displays the domain names that are configured for this service and match the certificate.

    **Note:**

    -   The domain name list displays the domain names on which the certificate can be deployed only when domain names match the certificate and are configured for the Alibaba Cloud service.
    -   If the certificate that you want to deploy to a CLB instance or an ALB instance does not meet the specified requirements, the domain name list is empty. For more information about the requirements, see [Limits on certificate deployment on a CLB instance or an ALB instance](#section_stm_ojt_doh).
5.  In the domain name list, select the domain name to which you want to deploy the certificate. Then, deploy the certificate to the domain name with a few clicks.

    You can deploy the certificate by using one of the following methods:

    -   Click **Deploy All** to deploy the certificate to all domain names.
    -   Select multiple domain names to which you want to deploy the certificate. Then, click **Batch Deploy** below the domain name list to deploy the certificate to the selected domain names.
    -   Find the domain name to which you want to deploy the certificate and click **Deploy** in the **Actions** column to deploy the certificate to the domain name.
    After the certificate is deployed, the value of the **Deployed** parameter for the domain name changes to **Yes**. In addition, the values of the **Deployed** and **Undeployed** parameters above the domain name list are also automatically updated.

6.  After the certificate is deployed, close the **Deploy Certificate** panel.

7.  View the status of certificate deployment.

    In the certificate list, find the certificate and click **Details** in the **Actions** column to view the status of the certificate deployment. In the **Certificate Details** panel, the **Deployed** section in the lower part shows the Alibaba Cloud services and domain names to which the certificate is deployed.


