# Deploy certificates on Alibaba Cloud services

After a certificate is issued, you can deploy it on an Alibaba Cloud service with a few clicks.

You can deploy certificates on the following Alibaba Cloud services. More services will be supported.

-   Server Load Balancer \(SLB\)
-   Alibaba Cloud CDN \(CDN\)
-   Secure CDN \(SCDN\)
-   Dynamic Route for CDN \(DCDN\)

**Note:** You can deploy certificates on Alibaba Cloud services only after the certificates are issued.

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  On the SSL Certificates page, find the certificate that you want to deploy in the Issued certificate list, and click **Deploy**.

3.  In the Deploy drop-down list, select the Alibaba Cloud service on which you want to deploy the certificate.

    ![Alibaba Cloud service on which you want to deploy the certificate](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5283807061/p111871.png)

4.  In the **Deploy Certificate** panel, select regions or domain names to deploy the certificate.

    **Note:**

    -   If you want to deploy the certificate on an SLB instance, select the region of the SLB instance. You can select multiple regions.
    -   If you want to deploy the certificate on a CDN, SCDN, or DCDN instance, select the domain names that are added to the instances. You can select multiple domain names.
5.  Click **Deploy**.


After you deploy the certificate on the Alibaba Cloud service, you can click **Details** of the certificate. In the **Certificate Details** panel, you can view the details about the certificate and the Alibaba Cloud service on which the certificate is deployed.

![Certificate details](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6809407951/p33415.png)

**Related topics**  


[Configure a multi-domain-name HTTPS website on an SLB instance](/intl.en-US/Tutorials/Configure a multi-domain-name HTTPS website on an SLB instance.md)

