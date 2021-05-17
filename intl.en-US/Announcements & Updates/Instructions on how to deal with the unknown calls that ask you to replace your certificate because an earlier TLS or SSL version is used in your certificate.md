# Instructions on how to deal with the unknown calls that ask you to replace your certificate because an earlier TLS or SSL version is used in your certificate

Dear users,

If you receive unknown calls that ask you to purchase a new certificate to replace your existing certificate because an earlier or incompatible TLS or SSL version is used in your certificate, ignore the calls. For example, the caller may state that the version TLS 1.0, SSL 1.0, or SSL 2.0 you use is too outdated to have the security protection capabilities you require, or the caller may state that TLS 1.3 is incompatible with your certificate.

If your certificate is purchased from and issued at the SSL Certificates Service console, your certificate is compatible with all TLS and SSL versions. By default, the versions TLS 1.0, 1.1, 1.2, and 1.3 are all supported. Furthermore, SSL Certificates Service allows you to specify the TLS or SSL versions when you deploy your certificate to web servers.

For example, you can exclude TLS 1.0 from the configuration of SSL protocols when you deploy a certificate to a web server because this version delivers lower security than other TLS versions. Then, the web server rejects requests from the clients that use TLS 1.0. You can also modify the configuration of SSL protocols by adding TLS 1.3. The configuration method varies based on the type of web server. For more information, see [How can I install SSL certificates?](/intl.en-US/Install Certificates/How can I install SSL certificates?.md)

