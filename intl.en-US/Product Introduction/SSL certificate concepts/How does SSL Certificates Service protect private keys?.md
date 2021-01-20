---
keyword: [Alibaba Cloud, SSL Certificates Service, Private key protection]
---

# How does SSL Certificates Service protect private keys?

SSL Certificates Service encrypts and stores private keys for SSL certificates by using Alibaba Cloud Key Management Service \(KMS\) to protect the security of your private keys.

SSL Certificates Service uses accredited KMS to encrypt and store the private keys uploaded with your SSL certificates and the private keys generated with certificate signing requests \(CSRs\) during your certificate application.

KMS is a security management service that ensures the security, integrity, and availability of keys for certificates. This service allows you to manage keys for multiple applications and services while meeting regulatory and cybersecurity classified protection requirements. For more information about KMS, see [What is Key Management Service?](/intl.en-US/Product Introduction/What is Key Management Service?.md).

SSL Certificates Service stores private keys for certificates by using various asymmetric encryption methods. The plaintext of a private key is never stored in disks, and appears in the application memory only when necessary. For example, when you download a certificate, SSL Certificates Service decrypts the ciphertext of the private key for this certificate. In this way, the decrypted ciphertext appears as plaintext in your server memory and can be downloaded to your local computer over HTTPS.

