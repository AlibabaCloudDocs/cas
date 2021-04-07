# How do I set the TLS version of my certificate?

Supported TLS versions are TLSv1.0, TLSv1.1, and TLSv1.2. You can set the TLS version on your Alibaba Cloud services and web servers as required.

If your certificate is installed on the following Alibaba Cloud services, set the TLS version by referring to the respective links:

-   SLB: [Manage TLS security policies](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Manage TLS security policies.md)
-   CDN: [Configure TLS](/intl.en-US/Domain Management/HTTPS/Configure TLS.md)
-   DCDN: [Configure TLS]()

If your certificate is installed on a web server, find `ssl_protocols TLSv1 TLSv1.1 TLSv1.2` in the certificate configuration file and modify the settings as required. For example, if you want to use TLSv1.1 and TLSv1.2 in your certificate, remove `TLSv1` from `ssl_protocols TLSv1 TLSv1.1 TLSv1.2`.

