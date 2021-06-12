# What is SSL Certificates Service?

SSL Certificates Service is a digital certificate service provided by Alibaba Cloud in cooperation with certificate authorities \(CAs\) inside and outside China. This service allows you to purchase and deploy certificates in the SSL Certificates Service console. SSL Certificates Service allows you to redirect traffic to your websites or mobile applications from HTTP to HTTPS at minimal costs. You can use SSL certificates to authenticate users and encrypt data.

## Relationship between SSL Certificates Service and HTTPS

You can purchase an SSL certificate instance in the SSL Certificates Service console and submit a certificate application to a CA for certificate issuance. After you install an issued SSL certificate on your web server, the web service transmits data over HTTPS.

If HTTPS is supported for the web service, an encrypted channel over SSL is used to transmit data between a client browser and the web server. This enables bidirectional encrypted transmission and prevents data in transit from being tampered with or intercepted.

## Benefits of HTTPS support for websites

-   Prevents data hijacking, tampering, and eavesdropping. SSL certificates allow you to enable end-to-end HTTPS encryption on your website. This way, data is encrypted when users interact with your website.
-   Improves search engine rankings. If HTTPS encryption is enabled on your website, your website ranks higher in the search results. This improves the credibility of your website.
-   Increases website traffic. If HTTPS encryption is enabled on your website, your website gains more trust from users who want to access your website. This increases the traffic to your website.

## Features

The following table describes the features supported by SSL Certificates Service.

|Module|Feature|Description|References|
|------|-------|-----------|----------|
|SSL certificate issuance and use|Purchase SSL certificate instances|You can purchase SSL certificate instances in the SSL Certificate Service console. Then, you can use the instances to apply for Domain Validation \(DV\), Organization Validation \(OV\), and Extended Validation \(EV\) certificates. For more information, see [Supported certificate types](#section_alp_t7y_yly).

|[Purchase an SSL Certificates Service instance](/intl.en-US/Buy Certificates/Purchase an SSL Certificates Service instance.md) |
|Apply for certificates|You can use the purchased SSL certificate instances to apply for certificates. If certificate validation errors are returned by CAs, you must fix the errors in a timely manner.|[Apply for a certificate](/intl.en-US/Issue Certificates/Apply for a certificate.md)|
|Install certificates|You can download issued certificates to your computer and install the certificates on your web servers.|[t123605.md\#](/intl.en-US/Install Certificates/How can I install SSL certificates?.md)|
|You can deploy issued certificates to supported Alibaba Cloud services. This way, you do not need to upload certificates to and configure SSL certificates for these services. For more information, see [Supported Alibaba Cloud services](#section_i5v_dd4_g4f).

|[Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md)|
|Revoke certificates|You can revoke certificates in the SSL Certificates Service console after your revocation requests are approved by CAs. The process to revoke certificates is secure and fast.|[Revoke an SSL certificate](/intl.en-US/Revoke and Delete Certificates/Revoke an SSL certificate.md)|
|Request refunds for purchased certificates|You can request refunds for purchased SSL certificates in the SSL Certificates Service console if specific conditions are met.|[Request a refund for an SSL certificate](/intl.en-US/Refund/Request a refund for an SSL certificate.md)|
|Certificate renewal|Manually renew certificates|You can manually renew and update the certificates in the SSL Certificates Service console within 30 calendar days before your certificates expire.|[Manual renewal](/intl.en-US/Renew Certificates/Overview.md)|
|Private Certificate Authority \(PCA\)|Issue private certificates|PCA allows you to build a private CA for your enterprise in the SSL Certificates Service console. This private CA can issue and manage self-signed private certificates within the enterprise. Then, you can use the private certificates to authenticate the identities of applications and encrypt and decrypt data within the enterprise.|[Overview](/intl.en-US/Private Certificates/Overview.md)|
|Website security detection|Check websites|SSL Certificates Service automatically checks the website assets that belong to your Alibaba Cloud account and the status of the SSL certificates that are installed on your websites. After the check is complete, you can determine whether to enable HTTPS for your websites.|[View the status of SSL certificates](/intl.en-US/Website Security Check/View the status of SSL certificates.md)|
|Application information management|Manage contact information|SSL Certificates Service automatically saves the contact information that is used to apply for certificates as contacts. Alternatively, you can manually create contacts. This way, you can directly select existing contacts when you apply for certificates.|[Manage contacts](/intl.en-US/Contact Management/Manage contacts.md)|
|Manage company information|SSL Certificates Service automatically saves the company information that is used to apply for certificates as company profiles. Alternatively, you can manually create company profiles. This way, you can directly select existing company profiles when you apply for certificates.|[Manage company profiles](/intl.en-US/Contact Management/Manage company profiles.md)|
|Centralized certificate management|Upload certificates|You can upload existing certificates to the SSL Certificates Service console for centralized management. For example, you can deploy the certificates to Alibaba Cloud services with a few clicks.|[Upload certificates](/intl.en-US/Upload Certificates/Upload certificates.md)|

## Supported certificate types

SSL Certificates Service allows you to purchase DV, OV, and EV certificates. Different types of certificates provide different levels of security and are suitable for different types of websites.

|Certificate type|Applicable website|Credibility level|Authentication strength|Security|Available certificate brand|
|----------------|------------------|-----------------|-----------------------|--------|---------------------------|
|Domain Validation \(DV\) SSL|Websites of individuals|Moderate|Certificate authorities \(CAs\) verify the authenticity of a website, instead of an enterprise.|Moderate|GlobalSign|
|Organization Validation \(OV\) SSL|Websites of organizations such as governments, enterprises, and educational institutions|High|CAs verify the authenticity of an organization or an enterprise.|High|GlobalSign and Entrust|
|Extended Validation \(EV\) SSL|Websites of organizations such as large-sized enterprises and financial institutions|Highest|CAs perform strict authentication.|Highest \(The address bar is in green.\)|Entrust|

For more information, see [Certificate brands supported by Alibaba Cloud](/intl.en-US/Product Introduction/Supported certificate brands.md).

## Supported Alibaba Cloud services

When you use the Alibaba Cloud services that are described in the following table, you may need to upload and configure SSL certificates in the consoles of the services.

If you have purchased SSL certificates in the SSL Certificates Service console and the certificates are issued, or if you have uploaded third-party SSL certificates to the SSL Certificates Service console for centralized management, you can deploy the SSL certificates to some Alibaba Cloud services in the SSL Certificates Service console with a few clicks. You do not need to upload or configure the SSL certificates in the consoles of these services. The following table describes the services.

|Alibaba Cloud service|Description|Certificate deployment|
|---------------------|-----------|----------------------|
|[Anti-DDoS Pro and Anti-DDoS Premium](/intl.en-US/Product Introduction on Alibaba DDoS Protection/What are Anti-DDoS Pro and Anti-DDoS Premium?.md)|Anti-DDoS Pro and Anti-DDoS Premium are proxy-based services provided by Alibaba Cloud to mitigate volumetric DDoS attacks.|-   The quick deployment feature is not used:

If you want to use Anti-DDoS Pro or Anti-DDoS Premium to defend against HTTPS flood attacks, you must manually upload SSL certificates that are used by domain names in the Anti-DDoS Pro console. For more information, see [Upload an HTTPS certificate](/intl.en-US/Anti-DDoS Pro & Premium User Guide/Provisioning/Use domains/Upload an HTTPS certificate.md).

-   The quick deployment feature is used:

You can deploy an SSL certificate to Anti-DDoS Pro or Anti-DDoS Premium in the SSL Certificates Service console with a few clicks without the need to upload the SSL certificate in the Anti-DDoS Pro console. Then, the SSL certificate is automatically bound to the domain name that is protected by Anti-DDoS Pro or Anti-DDoS Premium. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |
|[Web Application Firewall \(WAF\)](/intl.en-US/Product Introduction/What is WAF?.md)|WAF is a security service provided by Alibaba Cloud to protect web applications against common attacks defined by the Open Web Application Security Project \(OWASP\) and mitigate HTTP flood attacks. This service protects your website assets against data leaks and ensures the security and availability of your websites.|-   The quick deployment feature is not used:

If you want to use WAF to prevent HTTPS flood attacks, you must manually upload SSL certificates that are used by domain names in the WAF console. For more information, see [Upload an HTTPS certificate](/intl.en-US/Website Access/Website access with CNAME/Add a website.md).

-   The quick deployment feature is used:

You can deploy an SSL certificate to WAF in the SSL Certificates Service console with a few clicks without the need to upload the SSL certificate in the WAF console. Then, the SSL certificate is automatically bound to the domain name that is protected by WAF. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |
|[Object Storage Service \(OSS\)](/intl.en-US/Product Introduction/What is OSS?.md)|OSS is a secure, cost-effective, and high-durability cloud storage service provided by Alibaba Cloud. OSS supports RESTful APIs that are independent of the console. You can store and access all types of data in any application, at any time, from anywhere.|-   The quick deployment feature is not used:

If you want to use HTTPS to access a custom domain name that is mapped to an OSS bucket, you must manually upload your SSL certificate in the OSS console. For more information, see [Host SSL certificates](/intl.en-US/Console User Guide/Manage buckets/Manage a domain/Host SSL certificates.md).

-   The quick deployment feature is used:

You can deploy an SSL certificate to OSS in the SSL Certificates Service console with a few clicks without the need to upload the SSL certificate in the OSS console. Then, the SSL certificate is automatically bound to your custom domain name. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |
|[Application Load Balancer \(ALB\)](/intl.en-US/Application Load Balancer/ALB Product Introduction/What is ALB?.md)|ALB is a fully managed online load balancing service provided by Alibaba Cloud. ALB supports Layer 7 load balancing and provides high-performance processing capabilities at Layer 7. ALB supports HTTP, HTTPS, and QUIC.|-   The quick deployment feature is not used:

If you want to use an ALB instance to forward HTTPS requests, you must add an HTTPS listener and configure an SSL certificate for the ALB instance. For more information, see [Add an HTTPS listener](/intl.en-US/Application Load Balancer/ALB User Guide/Listeners/Add an HTTPS listener.md).

-   The quick deployment feature is used:

You can deploy an SSL certificate to an ALB instance in the SSL Certificates Service console with a few clicks without the need to configure the SSL certificate in the ALB instance. Then, the SSL certificate is automatically bound to the domain name that has HTTPS listeners configured. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |
|[Classic Load Balancer \(CLB\)](/intl.en-US/Classic Load Balancer/Product Introduction/What is CLB?.md)|CLB is an on-demand traffic distribution service provided by Alibaba Cloud. CLB supports TCP, UDP, HTTP, and HTTPS, and provides robust processing capabilities at Layer 4 and basic processing capabilities at Layer 7.|-   The quick deployment feature is not used:

If you want to use a CLB instance to forward HTTPS requests, you must add an HTTPS listener and configure an SSL certificate for the CLB instance. For more information, see [Add an HTTPS listener](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Add an HTTPS listener.md).

-   The quick deployment feature is used:

You can deploy an SSL certificate to the CLB instance in the SSL Certificates Service console with a few clicks without the need to upload the SSL certificate to the CLB instance. Then, the SSL certificate is automatically bound to the domain name that has HTTPS listeners configured. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |
|[Alibaba Cloud Content Delivery Network \(CDN\)](/intl.en-US/Product Introduction/What is Alibaba Cloud CDN?.md)|Alibaba Cloud CDN is provided by Alibaba Cloud to offload network traffic from origin servers, prevent network congestion, and accelerate resource access. You can use Alibaba Cloud CDN to accelerate website content delivery in different regions and scenarios.|-   The quick deployment feature is not used:

If you want to use Alibaba Cloud CDN to implement HTTPS acceleration, you must configure an SSL certificate in the Alibaba Cloud CDN console. For more information, see [Configure an SSL certificate](/intl.en-US/Domain Management/HTTPS/Configure an SSL certificate.md).

-   The quick deployment feature is used:

You can deploy an SSL certificate to Alibaba Cloud CDN in the SSL Certificates Service console with a few clicks without the need to upload the SSL certificate. Then, the SSL certificate is automatically bound to the domain name that has HTTPS enabled in Alibaba Cloud CDN. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |
|[Dynamic Route for CDN \(DCDN\)]()|DCDN is a CDN service developed by Alibaba Cloud to accelerate static and dynamic content delivery. This service provides a solution to resolve issues of high latency, packet loss, and instability. These issues may occur due to various causes, such as unstable networks, unexpected traffic spikes, and network congestion. These issues may also occur if your website contains both static and dynamic content, content is delivered across network providers, or only one origin server is used. You can use DCDN to improve the overall performance of your website and accelerate content delivery to improve user experience.|-   The quick deployment feature is not used:

If you want to use DCDN to implement HTTPS acceleration, you must configure an SSL certificate in the DCDN console. For more information, see [Configure HTTPS certificates]().

-   The quick deployment feature is used:

You can deploy an SSL certificate to DCDN in the SSL Certificates Service console with a few clicks without the need to upload the SSL certificate in the DCDN console. Then, the SSL certificate is automatically bound to the domain name that has HTTPS enabled in DCDN. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |
|[ApsaraVideo Live](/intl.en-US/Product Introduction/What is ApsaraVideo Live?.md)|ApsaraVideo Live is an audio and video streaming platform provided by Alibaba Cloud. The platform is based on the next-generation content access and delivery network and large-scale, distributed, and real-time transcoding technology. The platform provides a live streaming service with quick access, high resolution, high fluency, low latency, and high concurrency.|-   The quick deployment feature is not used:

If you want to use the HTTPS secure acceleration feature of ApsaraVideo Live, you must configure an SSL certificate in the ApsaraVideo Live console. For more information, see [Enable HTTPS]().

-   The quick deployment feature is used:

You can deploy an SSL certificate to ApsaraVideo Live in the SSL Certificates Service console with a few clicks without the need to upload the SSL certificate in the ApsaraVideo Live console. Then, the SSL certificate is automatically bound to the domain name that has HTTPS secure acceleration enabled. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |

