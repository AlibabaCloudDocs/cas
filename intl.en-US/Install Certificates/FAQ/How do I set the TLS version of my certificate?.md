# How do I set the TLS version of my certificate?

TLS v1.0, TLS v1.1, TLS v1.2, and TLS v1.3 are available. A later version of TLS ensures higher security of HTTPS communication than an earlier version. However, a later version is less compatible with browsers than an earlier version. You can set the TLS version of the certificate that you install on your web server or Alibaba Cloud service based on your business needs.

If your certificate is installed on a web server, find `ssl_protocols TLSv1 TLSv1.1 TLSv1.2` in the certificate configuration file and modify the settings as needed. For example, if your certificate supports only TLS v1.1 and TLS v1.2, remove `TLSv1` from `ssl_protocols TLSv1 TLSv1.1 TLSv1.2`. If your certificate needs to support TLS v1.3, add `TLSv1.3` to `ssl_protocols TLSv1 TLSv1.1 TLSv1.2`.

If your certificate is installed on the following Alibaba Cloud services, set the TLS version based on the instructions in the corresponding topic:

-   Anti-DDoS Pro and Anti-DDoS Premium: [Create a custom TLS policy](/intl.en-US/Anti-DDoS Pro & Premium User Guide/Provisioning/Use domains/Create a custom TLS policy.md)
-   Web Application Firewall \(WAF\): [Configure custom TLS settings](/intl.en-US/Website Access/Configure custom TLS settings.md)
-   Server Load Balancer \(SLB\): [Manage TLS security policies](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Manage TLS security policies.md)
-   Alibaba Cloud CDN: [Configure TLS](/intl.en-US/Domain Management/HTTPS/Configure TLS.md)
-   Dynamic Route for CDN \(DCDN\): [Configure TLS]()

