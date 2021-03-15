# What is SSL Certificates Service?

SSL Certificates Service is a digital certificate service that is provided by Alibaba Cloud in cooperation with certificate authorities \(CAs\) inside and outside China. This service allows you to purchase and deploy certificates in the SSL Certificates Service console. SSL Certificates Service allows you to redirect traffic to your website or mobile applications from HTTP to HTTPS at minimal costs. You can use SSL certificates to authenticate users and encrypt data.

## Benefits of HTTPS support for websites

-   Prevents data hijacking, tampering, and eavesdropping. SSL certificates allow you to enable HTTPS encryption on your websites. Then, data is encrypted when users interact with your website.
-   Improves search engine rankings. If HTTPS encryption is enabled on your website, your website gains a higher ranking on the search engine result page. This improves the credibility of your website.
-   Increases web traffic. If HTTPS encryption is enabled on your website, your website is more trustworthy for users to access. This increases the traffic to your website.

## Features

The following table describes the features that SSL Certificates Service provides.

|Module|Feature|Description|Documentation|
|------|-------|-----------|-------------|
|HTTPS websites|Purchase certificate instances|You can purchase certificate instances in the SSL Certificate Service console. Then, you can use the certificate instances to apply for Domain Validation \(DV\), Organization Validation \(OV\), and Extended Validation \(EV\) certificates.For more information, see [Supported certificate types](#section_alp_t7y_yly).

|[Select and purchase certificates](/intl.en-US/Buy Certificates/Select and purchase certificates.md)|
|Apply for certificates|You can use the certificate instances that you purchase to apply for and issue certificates. If errors are returned by CAs, you must fix the errors in a timely manner.|[Apply for a certificate](/intl.en-US/Issue Certificates/Apply for a certificate.md)|
|Download certificates|You can download issued certificates to your computer and install them on your web servers.|[Download certificates](/intl.en-US/Install Certificates/Download certificates.md)|
|Deploy certificates|You can deploy issued certificates to Alibaba Cloud services with a few clicks.For more information, see [Related services](#section_i5v_dd4_g4f).

|[Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy certificates on Alibaba Cloud services.md)|
|Centralized certificate management|Upload certificates|You can upload existing certificates to the SSL Certificates Service console for centralized management. For example, you can deploy the certificates to Alibaba Cloud services with a few clicks.|[Upload certificates](/intl.en-US/Upload Certificates/Upload certificates.md)|
|Revoke certificates|You can revoke certificates in the SSL Certificates Service console after your revocation requests are approved by CAs. The process to revoke certificates is secure and fast.|[Revoke certificates](/intl.en-US/Revoke and Delete Certificates/Revoke certificates.md)|

## Supported certificate types

SSL Certificates Service supports DV, OV, and EV certificates. Different types of certificates provide different levels of security and are applicable to different websites.

|Certificate type|Applicable website|Credibility level|Authentication strength|Security|Available certificate brand|
|----------------|------------------|-----------------|-----------------------|--------|---------------------------|
|Domain Validation \(DV\) SSL|Websites of individuals|Moderate|Certificate authorities \(CAs\) verify the authenticity of a website, but does not verify the authenticity of an enterprise.|Moderate|GlobalSign|
|Organization Validation \(OV\) SSL|Websites of organizations such as governments, enterprises, and educational institutions|High|CAs verify the authenticity of an organization or an enterprise.|High|GlobalSign and Entrust|
|Extended Validation \(EV\) SSL|Websites of organizations such as large-sized enterprises and financial institutions|Highest|CAs perform strict authentication.|Highest \(The address bar is in green.\)|Entrust|

For more information about certificate brands, see [Brands of certificates supported by Alibaba Cloud](/intl.en-US/Buy Certificates/Select and purchase certificates.mdsection_hfl_s09_ij2).

## Related services

-   Anti-DDoS Pro and Anti-DDoS Premium: proxy-based services provided by Alibaba Cloud to mitigate volumetric DDoS attacks.

    For more information, see [What are Anti-DDoS Pro and Anti-DDoS Premium?](/intl.en-US/Product Introduction on Alibaba DDoS Protection/What are Anti-DDoS Pro and Anti-DDoS Premium?.md)

-   Web Application Firewall \(WAF\): a security service provided by Alibaba Cloud to protect web applications against common attacks defined by the Open Web Application Security Project \(OWASP\) and mitigate HTTP flood attacks. This service protects your website assets against data leaks and ensures the security and availability of website services.

    For more information, see [What is WAF?](/intl.en-US/Product Introduction/What is WAF?.md)

-   Alibaba Cloud CDN: a content delivery network provided by Alibaba Cloud to offload network traffic from origin servers and prevent network congestion. You can use Alibaba Cloud CDN to accelerate website content delivery in different regions and scenarios.

    For more information, see [What is Alibaba Cloud CDN?](/intl.en-US/Product Introduction/What is Alibaba Cloud CDN?.md)

-   Dynamic Route for CDN \(DCDN\): a CDN service developed by Alibaba Cloud to accelerate static and dynamic content delivery. This service provides a solution to resolve issues of high latency, packet loss, and instability. These issues may occur for various reasons, such as unstable networks, unexpected traffic spikes, and network congestion. These issues may also occur if your website contains both static and dynamic content, content is delivered across network providers, or only one origin server is used. You can use DCDN to improve the overall performance of your website and accelerate content delivery to improve user experience.

    For more information, see [What is Dynamic Route for CDN?]()

-   ApsaraVideo Live: an audio and video streaming platform provided by Alibaba Cloud. The platform is based on the next-generation content access and delivery network and large-scale, distributed, and real-time transcoding technology. The platform provides a live streaming service with quick access, high resolution, high fluency, low latency, and high concurrency.

    For more information, see [What is ApsaraVideo Live](/intl.en-US/Product Introduction/What is ApsaraVideo Live?.md).


