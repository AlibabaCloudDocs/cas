# What is SSL Certificates Service?

SSL Certificates Service is a digital certificate service that is provided by Alibaba Cloud in cooperation with certificate authorities \(CAs\) inside and outside China. This service allows you to purchase and deploy certificates in the SSL Certificates Service console. SSL Certificates Service allows you to redirect traffic to your website or mobile applications from HTTP to HTTPS at minimal cost. You can use SSL certificates for identity authentication and data encryption.

## Relationship between SSL Certificates Service and HTTPS

You can purchase SSL certificates in the SSL Certificates Service console, submit a certificate application to a certificate authority \(CA\), and then wait until the certificate is issued. After you install the issued SSL certificate on your web server, the web service transmits data over HTTPS.

After the SSL certificate is deployed on a web server, you can enable HTTPS to activate the SSL encrypted channel between a client browser and the web server. This enables bidirectional encrypted transmission and prevents data tampering or interception.

## Benefits of HTTPS support for websites

-   Prevents data hijacking, tampering, and eavesdropping. SSL certificates allow you to enable HTTPS encryption on your websites. Then, data is encrypted when users interact with your website.
-   Improves search engine rankings. If HTTPS encryption is enabled on your website, your website gains a higher ranking on the search engine result page. This improves the credibility of your website.
-   Increases website traffic. If HTTPS encryption is enabled on your website, your website is more trustworthy for users to access. This increases the traffic to your website.

## Features

The following table describes the features supported by SSL Certificates Service.

|Module|Feature|Description|References|
|------|-------|-----------|----------|
|SSL certificate issuance and use|Allows you to purchase SSL Certificates Service instances.|You can purchase SSL Certificates Service instances in the SSL Certificate Service console. Then, you can use the instances to apply for Domain Validation \(DV\), Organization Validation \(OV\), and Extended Validation \(EV\) certificates. For more information, see [Supported certificate types](#section_alp_t7y_yly).

|[Select and purchase certificates](/intl.en-US/Buy Certificates/Select and purchase certificates.md) |
|Allows you to apply for certificates.|You can use the purchased SSL Certificates Service instance to submit a certificate application and handle the audit exception until the CA issues the certificate for you.|[Apply for a certificate](/intl.en-US/Issue Certificates/Apply for a certificate.md)|
|Allows you to install certificates.|You can download issued certificates to on-premises computers and install them on your web servers.|[How can I install SSL certificates?](/intl.en-US/Install Certificates/How can I install SSL certificates?.md)|
|To enable HTTPS encryption for an Alibaba Cloud service, you can directly deploy an issued Alibaba Cloud SSL certificate to the service with a few clicks, without the need to upload a certificate first. For more information, see [Related services](#section_i5v_dd4_g4f).

|[Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md)|
|Allows you to revoke certificates.|You can revoke certificates in the SSL Certificates Service console after your revocation requests are approved by CAs. The process to revoke certificates is secure and fast.|[Revoke certificates](/intl.en-US/Revoke and Delete Certificates/Revoke certificates.md)|
|Allows you to request refunds for purchased certificates.|You can request a refund for a purchased SSL certificate in the SSL Certificates Service console if specific conditions are met.|[Refund instructions](/intl.en-US/Refund/Refund instructions.md)|
|Certificate renewal|Allows you to manually renew certificates.|Within 30 natural days before your certificate expires, you can manually renew and update the certificate in the SSL Certificates Service console.|[Manual renewal](/intl.en-US/Renew Certificates/Overview.md)|
|Website security detection|Detects website security.|SSL Certificates Service automatically detects the website assets that belong to your Alibaba Cloud account and check the status of the SSL certificates that are installed on your websites. You can also enable HTTPS on your websites in a more convenient way.|[View the status of SSL certificates](/intl.en-US/Website Security Check/View the status of SSL certificates.md)|
|Application information management|Manages contact information.|SSL Certificates Service automatically saves the contact information that you have used in a certificate application, or you can manually add contacts. This way, you can directly select the existing contacts when you apply for a certificate.|[Manage contacts](/intl.en-US/Contact Management/Manage contacts.md)|
|Manages company information.|SSL Certificates Service automatically saves the company information that you have used in a certificate application, or you can manually add companies. This way, you can directly select the existing company when you apply for a certificate.|[Manage company profiles](/intl.en-US/Contact Management/Manage company profiles.md)|
|Centralized certificate management|Allows you to upload certificates.|You can upload existing certificates to the SSL Certificates Service console for centralized management. For example, you can deploy the certificates to Alibaba Cloud services with a few clicks.|[Upload certificates](/intl.en-US/Upload Certificates/Upload certificates.md)|

## Supported certificate types

SSL Certificates Service supports DV, OV, and EV certificates. Different types of certificates provide different levels of security and are applicable to different types of websites.

|Certificate type|Applicable website|Credibility level|Authentication strength|Security|Available certificate brand|
|----------------|------------------|-----------------|-----------------------|--------|---------------------------|
|Domain Validation \(DV\) SSL|Websites of individuals|Moderate|Certificate authorities \(CAs\) verify the authenticity of a website, but does not verify the authenticity of an enterprise.|Moderate|GlobalSign|
|Organization Validation \(OV\) SSL|Websites of organizations such as governments, enterprises, and educational institutions|High|CAs verify the authenticity of an organization or an enterprise.|High|GlobalSign and Entrust|
|Extended Validation \(EV\) SSL|Websites of organizations such as large-sized enterprises and financial institutions|Highest|CAs perform strict authentication.|Highest \(The address bar is in green.\)|Entrust|

For more information, see [Certificate brands supported by Alibaba Cloud](/intl.en-US/Product Introduction/Supported certificate brands.md).

## Related services

When you use the Alibaba Cloud services described in the following table, you may need to upload and configure SSL certificates in the consoles of the corresponding services.

Assume that you have purchased and issued SSL certificates in the SSL Certificates Service console or uploaded SSL certificates purchased on third-party platforms to the SSL Certificates Service console for centralized management. You can deploy the SSL certificates to the following Alibaba Cloud services in the SSL Certificates Service console instead of uploading and configuring the SSL certificates in the consoles of the corresponding Alibaba Cloud services.

|Alibaba Cloud service|Description|Certificate deployment|
|---------------------|-----------|----------------------|
|[Anti-DDoS Pro and Anti-DDoS Premium](/intl.en-US/Product Introduction on Alibaba DDoS Protection/What are Anti-DDoS Pro and Anti-DDoS Premium?.md)|Anti-DDoS Pro and Anti-DDoS Premium are proxy-based services provided by Alibaba Cloud to mitigate volumetric DDoS attacks.|-   The quick deployment feature is not used:

If you need to use Anti-DDoS Pro or Anti-DDoS Premium to defend against HTTPS flood attacks, manually upload an SSL certificate that is used by the website domain names in the Anti-DDoS Pro console. For more information, see [Upload an HTTPS certificate](/intl.en-US/Anti-DDoS Pro & Premium User Guide/Provisioning/Use domains/Upload an HTTPS certificate.md).

-   The quick deployment feature is used:

Instead of uploading an SSL certificate in the Anti-DDoS Pro console, you can deploy an SSL certificate to Anti-DDoS Pro or Anti-DDoS Premium in the SSL Certificates Service console with a few clicks. Then, the SSL certificate is automatically associated with the domain names that have Anti-DDoS Pro or Anti-DDoS Premium enabled. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |
|[Web Application Firewall \(WAF\)](/intl.en-US/Product Introduction/What is WAF?.md)|WAF is a security service provided by Alibaba Cloud to protect web applications against common attacks defined by the Open Web Application Security Project \(OWASP\) and mitigate HTTP flood attacks. This service protects your website assets against data leaks and ensures the security and availability of website services.|-   The quick deployment feature is not used:

If you need to use WAF to prevent HTTPS request attacks, you must manually upload an SSL certificate used by the website domain names in the WAF console. For more information, see [Upload HTTPS certificates](/intl.en-US/Website Access/Website access with CNAME/Add websites.md).

-   The quick deployment feature is used:

Instead of uploading an SSL certificate in the WAF console, you can deploy an SSL certificate to WAF in the SSL Certificates Service console with a few clicks. Then, the SSL certificate is automatically associated with the domain names that have WAF enabled. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |
|[Application Load Balancer \(ALB\)](/intl.en-US/Application Load Balancer/What is Application Load Balancer (ALB)?.md)|ALB is a fully managed online load balancer service provided by Alibaba Cloud. ALB supports Layer 7 load balancing and provides high-performance processing capabilities at Layer 7. ALB supports the HTTP, HTTPS, and QUIC protocols.|-   The quick deployment feature is not used:

If you need to use an ALB instance to forward HTTPS requests, you must add an HTTPS listener and configure an SSL certificate for the ALB instance. For more information, see [Add an HTTPS listener](/intl.en-US/Application Load Balancer/Application Load Balancer Listener/Add an HTTPS listener.md).

-   The quick deployment feature is used:

Instead of configuring an SSL certificate for the ALB instance, you can deploy an SSL certificate to the ALB instance in the SSL Certificates Service console with a few clicks. Then, the SSL certificate is automatically associated with the domain names that have HTTPS listeners enabled. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |
|[Classic Load Balancer \(CLB\)](/intl.en-US/Classic Load Balancer/Product Introduction/What is CLB?.md)|CLB distributes traffic to Elastic Compute Service \(ECS\) instances based on configurations. CLB supports the TCP, UDP, HTTP, and HTTPS protocols, and provides robust processing capabilities at Layer 4 and basic processing capabilities at Layer 7.|-   The quick deployment feature is not used:

If you need to use a CLB instance to forward HTTPS requests, you must add an HTTPS listener and configure an SSL certificate for the CLB instance. For more information, see [Add an HTTPS listener](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Add an HTTPS listener.md).

-   The quick deployment feature is used:

Instead of configuring an SSL certificate for the CLB instance, you can deploy an SSL certificate to the CLB instance in the SSL Certificates Service console with a few clicks. Then, the SSL certificate is automatically associated with the domain names that have HTTPS listeners enabled. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |
|[Alibaba Cloud CDN](/intl.en-US/Product Introduction/What is Alibaba Cloud CDN?.md)|Alibaba Cloud CDN is a content delivery network \(CDN\) provided by Alibaba Cloud to offload network traffic from origin servers and prevent network congestion. You can use Alibaba Cloud CDN to accelerate website content delivery in different regions and scenarios.|-   The quick deployment feature is not used:

If you need to use Alibaba Cloud CDN to accelerate HTTPS requests, you must configure an HTTPS-based SSL certificate in the Alibaba Cloud CDN console. For more information, see [Configure an SSL certificate](/intl.en-US/Domain Management/HTTPS/Configure an SSL certificate.md).

-   The quick deployment feature is used:

Instead of uploading an SSL certificate in the Alibaba Cloud CDN console, you can deploy an SSL certificate to Alibaba Cloud CDN in the SSL Certificates Service console with a few clicks. Then, the SSL certificate is automatically associated with the domain names that have HTTPS enabled. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |
|[Dynamic Route for CDN \(DCDN\)]()|DCDN is a CDN service developed by Alibaba Cloud to accelerate static and dynamic content delivery. This service provides a solution to resolve issues of high latency, packet loss, and instability. These issues may occur for various reasons, such as unstable networks, unexpected traffic spikes, and network congestion. These issues may also occur if your website contains both static and dynamic content, content is delivered across network providers, or only one origin server is used. You can use DCDN to improve the overall performance of your website and accelerate content delivery to improve user experience.|-   The quick deployment feature is not used:

If you need to use DCDN to accelerate HTTPS requests, you must configure an HTTPS-based SSL certificate in the DCDN console. For more information, see [Configure HTTPS certificates]().

-   The quick deployment feature is used:

Instead of uploading an SSL certificate in the DCDN console, you can deploy an SSL certificate to DCDN in the SSL Certificates Service console with a few clicks. Then, the SSL certificate is automatically associated with the domain names that have DCDN enabled. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |
|[ApsaraVideo Live](/intl.en-US/Product Introduction/What is ApsaraVideo Live?.md)|ApsaraVideo Live is an audio and video streaming platform provided by Alibaba Cloud. The platform is based on the next-generation content access and delivery network and large-scale, distributed, and real-time transcoding technology. The platform provides a live streaming service with quick access, high resolution, high fluency, low latency, and high concurrency.|-   The quick deployment feature is not used:

If you need to use the HTTPS secure acceleration feature of ApsaraVideo Live, you must configure an HTTPS-based SSL certificate in the ApsaraVideo Live console. For more information, see [Enable HTTPS]().

-   The quick deployment feature is used:

Instead of uploading an SSL certificate in the ApsaraVideo Live console, you can deploy an SSL certificate to ApsaraVideo Live in the SSL Certificates Service console with a few clicks. Then, the SSL certificate is automatically associated with the domain names that have HTTPS secure acceleration enabled. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md). |

