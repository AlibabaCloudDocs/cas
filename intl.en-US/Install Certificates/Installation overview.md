# Installation overview

After you purchase an SSL certificate in the SSL Certificates Service console and the certificate is issued, you can download the certificate from the console to your computer and install the certificate. The certificate can be installed on a web server or deployed to a supported Alibaba Cloud service.

An SSL certificate is purchased and issued by using SSL Certificates Service. For more information, see [Purchase an SSL Certificates Service instance](/intl.en-US/Buy Certificates/Purchase an SSL Certificates Service instance.md) and [Apply for a certificate](/intl.en-US/Issue Certificates/Apply for a certificate.md).

## Installation scenarios

|Scenario|Description|Process overview|
|--------|-----------|----------------|
|Installation on a web server|Install an SSL certificate on a web server and enable HTTPS listening to implement HTTPS communication between the server and clients. Different types of web servers support different formats of certificate files. To facilitate certificate installation, SSL Certificates Service provides certificate packages that are suitable for mainstream web servers, such as NGINX, Apache Tomcat, Apache HTTPD, and Internet Information Services \(IIS\) servers. You can download and use the packages without the need to convert the formats of certificate files.

|1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas) and download the files of an issued certificate to your computer.

You can download certificate files in the required format based on the type of your web server. For more information, see [Download a certificate to your computer](#section_cjh_359_s85).

2.  Upload the certificate files to your web server, modify server settings, and then enable HTTPS listening.

The settings vary based on web servers. SSL Certificates Service supports different methods to install SSL certificates on mainstream web servers. For more information, see [Install the certificate on your web server](#section_ri1_ayr_evy). |
|Deployment to an Alibaba Cloud service|Deploy an SSL certificate to specific resources of Alibaba Cloud services by using the SSL Certificates Service console. This simplifies certificate configuration. You can use this method to deploy an SSL certificate only to the following Alibaba Cloud services: Web Application Firewall \(WAF\), Object Storage Service \(OSS\), Classic Load Balancer \(CLB\), Application Load Balancer \(ALB\), Alibaba Cloud CDN, Secure CDN \(SCDN\), Dynamic Route for CDN \(DCDN\), ApsaraVideo Live, Anti-DDoS Pro, and Anti-DDoS Premium. CLB is formerly known as Service Load Balancer \(SLB\). For more information, see [Supported Alibaba Cloud services](/intl.en-US/Product Introduction/What is SSL Certificates Service?.md).

|Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas) and click **Deploy** to deploy an issued certificate to specific resources of Alibaba Cloud services. For more information, see [Deploy certificates to Alibaba Cloud services](/intl.en-US/Install Certificates/Deploy certificates to Alibaba Cloud services.md).|

## Download a certificate to your computer

If you have purchased a certificate in the SSL Certificates Service console and the certificate is issued, you can perform the following steps to download the certificate to your computer.

**Note:** For data security purposes, you are not allowed to download the third-party certificates that you upload to SSL Certificates Service.

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  In the certificate list, find the certificate that you want to download and click **Download** in the **Actions** column.

    **Note:** The **Download** button appears in the **Actions** column only when the certificate is in the **Issued**, **Pending Expiration**, or **Expired** state. If the certificate is in a different state, the **Download** button does not appear.

3.  In the **Download Certificate** panel, download the certificate for your web server.

    SSL Certificates Service automatically converts the certificate files into different formats that are suitable for various types of web servers and compresses the files into packages. Each package meets all the configuration requirements for a specific type of web server. You need only to click **Download** for your server type. Then, the certificate package is downloaded to your computer.

    ![Download Certificate ](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9677233261/p276585.png)

    Examples:

    -   If you use an Apache Tomcat server, you must download the certificate package in the PFX or JKS format.
        -   Click **Download** next to **Tomcat** to download a PFX certificate package.
        -   Click **Download** next to **JKS** to download a JKS certificate package.
    -   If you use an Apache HTTPD, NGINX, or IIS server, click **Download** next to **Apache**, **Nginx**, or **IIS**.
    -   If you use a different server, click **Download** next to **Other**.
    -   If you want to deploy a certificate to an Alibaba Cloud service, we recommend that you use the certificate deployment feature. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy certificates to Alibaba Cloud services.md). If the Alibaba Cloud service is not supported by SSL Certificates Service, we recommend that you download a certificate package suitable for NGINX servers by clicking **Download** next to **Nginx**.
    -   If you want to install a root certificate on clients, such as apps or Java clients, click **Download** next to **Download Root Certificate**.

        **Note:** If your web services are accessed by using client browsers, you do not need to manually install root certificates because the root certificates are built into the client browsers.

    After the download, the certificate package is stored in the default download directory of your browser. You can view the downloaded certificate package in the directory and decompress the package to obtain certificate files.


## Install the certificate on your web server

After you download the certificate to your computer, you must upload the certificate to your web server and modify the server settings for the certificate to take effect.

The operations to install a certificate vary based on web servers. The following table lists the methods to install a certificate on mainstream web servers.

|Web server type|Certificate installation method|
|---------------|-------------------------------|
|NGINX and Tengine|[Install an SSL certificate on an NGINX server or a Tengine server](/intl.en-US/Install Certificates/Install certificates to servers/Install an SSL certificate on an NGINX server or a Tengine server.md)|
|Apache Tomcat 7 and earlier|-   [Install .pfx SSL certificates](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md)
-   [Install .jks SSL certificates](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates in Tomcat servers/Install .jks SSL certificates.md) |
|Apache Tomcat 8 and later|[Deploy SSL certificates on Tomcat 8.5 or 9.0 servers that run CentOS](/intl.en-US/Install Certificates/Install certificates to servers/Deploy SSL certificates on Tomcat 8.5 or 9.0 servers that run CentOS.md)|
|Apache HTTPD|[Install SSL certificates on Apache servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates on Apache servers.md)|
|Apache 2|[Deploy SSL certificates on Apache 2 servers that run Ubuntu](/intl.en-US/Install Certificates/Install certificates to servers/Deploy SSL certificates on Apache 2 servers that run Ubuntu.md)|
|IIS|[Install SSL certificates on IIS servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates on IIS servers.md)|
|Jetty|[Install SSL certificates on Jetty servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates on Jetty servers.md)|
|JBoss|[Install SSL certificates on JBoss servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates on JBoss servers.md)|
|GlassFish|[Install SSL certificates on GlassFish servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates on GlassFish servers.md)|

