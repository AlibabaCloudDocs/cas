# 如何设置证书的TLS协议版本？

TLS协议版本包括TLS v1.0、TLS v1.1、TLS v1.2和TLS v1.3。您可以根据需要在Web服务器或阿里云产品上设置证书的TLS协议版本。

如果您的证书安装在Web服务器上，请在Web服务器的证书配置文件中找到`ssl_protocols TLSv1 TLSv1.1 TLSv1.2`，根据实际需要进行修改。例如，如果您的证书只支持TLS v1.1和TLS v1.2，在`ssl_protocols TLSv1 TLSv1.1 TLSv1.2`中去掉`TLSv1`；如果您的证书需要支持TLS v1.3，在`ssl_protocols TLSv1 TLSv1.1 TLSv1.2`中增加`TLSv1.3`。

如果您的证书部署在以下阿里云产品，请参见以下链接进行设置：

-   DDoS高防：[自定义TLS安全策略](/intl.zh-CN/DDoS高防（新BGP&国际）用户指南/接入DDoS高防/网站配置/自定义TLS安全策略.md)
-   Web应用防火墙：[自定义TLS配置](/intl.zh-CN/接入WAF/自定义TLS配置.md)
-   SLB：[TLS安全策略说明](/intl.zh-CN/传统型负载均衡CLB/CLB用户指南/监听/TLS安全策略说明.md)
-   CDN：[配置TLS](/intl.zh-CN/域名管理/HTTPS配置/配置TLS.md)
-   DCDN：[配置TLS]()

