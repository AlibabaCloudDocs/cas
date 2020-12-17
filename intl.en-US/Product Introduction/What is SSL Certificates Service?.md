# What is SSL Certificates Service?

SSL Certificates Service is a digital server certificate service provided by Alibaba Cloud. This service provides digital server certificates issued by certification authorities \(CAs\) both inside and outside China on the Alibaba Cloud platform. You can purchase the certificates you need on the Alibaba Cloud platform. Then, deploy these certificates in Alibaba Cloud products to convert your service from HTTP to HTTPS at minimal cost. This enables your websites to implement identity verification and data transmission encryption.

## Features

|Module|Value provided|Description|
|------|--------------|-----------|
|HTTPS-based websites|Prevents hijacking, tampering, and listening.|SSL Certificates Service allows you to enable HTTPS encryption on your websites. It encrypts the data throughout the interaction and access process between users and websites, preventing data hijacking, tampering, and listening.|
|Improves the search ranking of your website.|Using SSL certificates for HTTPS encryption improves the search results ranking of your website. This brings your website to the top of the search results and increases its trust.|
|Increases website traffic.|Using SSL certificates to build an HTTPS website increases user confidence and draws more traffic to your website.|
|Efficient certificate management|Improves certificate O&M efficiency.|By allowing you to upload certificates and private keys, SSL Certificates Service enables you to centrally manage various digital certificates on the Alibaba Cloud platform for greater O&M efficiency. You can submit them for review, view their domain names and expiration dates, modify certificate names, delete expired certificates, and more.|
|Deploys SSL certificates to other Alibaba Cloud products in one click.|SSL Certificates Service allows you to deploy SSL certificates to other Alibaba Cloud products on the Alibaba Cloud platform at minimal cost.|
|Revokes certificates easily.|According to the standardized revocation process, SSL Certificates Service provides a safe and quick way to revoke server SSL certificates that have been verified by CAs.|

## Concepts

The following introduces concepts relevant Alibaba Cloud SSL Certificates Service.

-   **What is a digital certificate?**

    A digital certificate is a document signed by a trusted CA. The certificate contains information about the public key owner and the public key file. It is a trusted credential issued by a CA to the website. The simplest certificate contains a public key, a certificate name, and a digital signature signed by a CA.

    An important feature of digital certificates is that they are only valid for a specific period of time.

-   **What is SSL?**

    SSL is a security protocol that implements network communication encryption. SSL establishes an encrypted channel between a browser and a website to prevent data tampering or interception during transmission.

-   **What is an SSL certificate?**

    An SSL certificate is a trusted certificate issued to a website by a CA, which uses the SSL protocol for communication.

    SSL Certificates Service uses a public-key encryption system that uses a matching key pair to encrypt and decrypt data. Each user creates a private key that is highly secured and not disclosed to anyone for decryption and signature. Meanwhile, the user creates a public key and discloses this key to a group of users for encryption and signature verification.

    After an SSL certificate is deployed on a web server, HTTPS is enabled for the web server. Your website will transmit data through HTTPS, which helps the web server and the website establish a trusted, encrypted connection to ensure the security of data during transmission.

    For more information about the private keys of certificates, see [What is a public key and a private key?](/intl.en-US/Product Introduction/SSL certificate concepts/What is a public key and a private key?.md).

-   **What is HTTPS?**

    Hypertext Transfer Protocol Secure \(HTTPS\) is a HTTP + SSL protocol. It is a secure version of the HTTP protocol that encrypts website communications based on the SSL protocol.

    After the SSL certificate is deployed on a website, you can enable HTTPS to activate **the SSL encrypted channel** \(SSL protocol\) between a client browser and the website server. This enables bidirectional encrypted transmission and prevents content tampering or interception.

-   **What is a CA?**

    CA stands for certification authority.

    As a trusted third party in an e-commerce transaction, the CA is responsible for verifying the validity of the public keys in the public key system.


