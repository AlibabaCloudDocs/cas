# Download a root certificate

This topic provides the links required to download the root certificates provided by specific certificate authorities \(CAs\). You can download and install the root certificates based on your business requirements. The CAs include DigiCert and GlobalSign.

## Scenarios

If your web services are accessed by using client browsers, you do not need to manually install root certificates because the root certificates are built into the client browsers. In this situation, you need only to install the Secure Sockets Layer \(SSL\) certificates issued by CAs on your web server. This way, your web server can communicate with the client browsers over HTTPS. For more information about how to install SSL certificates, see [t123605.md\#](/intl.en-US/Install Certificates/How can I install SSL certificates?.md).

If your web services are accessed by using other clients, such as apps or Java clients, you must manually install root certificates on the clients because no root certificates are built into the clients. If you do not install the root certificates in this situation, the clients cannot verify the information encrypted by your web server. For example, if your web server is installed with a DigiCert Organization Validation \(OV\) SSL certificate, the clients must be installed with DigiCert OV root certificates before they can communicate with your web server over HTTPS.

**Warning:** After you install root certificates on clients, the clients can verify the identity of the server but may still encounter web service interruptions due to specific issues. For example, the root certificates expired, became invalid, or underwent policy changes. Therefore, we do not recommend this method. If you still want to install the root certificates on apps or Java clients regardless of the risks, you can download the required root certificates from the links provided in the [Download links for root certificates](#section_hve_mh4_1gv) section of this topic.

We recommend that you implement client verification by using the default Truststore of the clients and enable strong domain name verification to enhance the security of the apps and Java clients. If you want to learn more information, submit a [ticket](https://ticket-intl.console.aliyun.com/#/ticket/add/?productId=80) or contact after-sales support engineers in the DingTalk service group.

## Download links for root certificates

-   [DigiCert EV root certificate](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/170239/cn_zh/1597374203590/Digicert-EV-root.cer)
-   [DigiCert OV and DV root certificates](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/170239/cn_zh/1597374262030/Digicert-OV-DV-root.cer)
-   [GlobalSign DV and OV root certificates](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/182164/cn_zh/1620365676642/GlobalSign-DV%26OV-root.cer)

**Note:** You cannot download Entrust root certificates.

