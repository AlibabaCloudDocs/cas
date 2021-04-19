# Terms

This topic introduces the terms used in Alibaba Cloud SSL Certificates Service.

## Digital certificate

A digital certificate is a document signed by a trusted certificate authority \(CA\). The certificate contains information about the public key owner and the public key file. It is a trusted credential that is issued by a CA to a website. A certificate must contain a public key, a certificate name, and a digital signature provided by a CA.

Digital certificates are valid only for a specific period of time.

## CA

CA stands for certificate authority.

As a trusted third party in an e-commerce transaction, a CA is responsible for verifying the validity of public keys.

## Certificate validity period

As of September 1, 2020, certificates issued by global CAs are valid for up to one year. The certificates you apply for by using SSL Certificates Service are valid for one year.

## SSL

Secure Sockets Layer \(SSL\) is a protocol that is used to encrypt data transmitted between browsers and websites over a network. It prevents data tampering or interception during data transmission.

## SSL certificate

An SSL certificate is a trusted credential that is issued by a CA to a website. It uses the SSL protocol for communications and implements website authentication and encrypted transmission.

SSL certificates provide a layered data security mechanism between TCP/IP and application protocols, such as HTTP, Telnet, and FTP. SSL uses public keys to encrypt data transmitted over TCP/IP connections, ensure message integrity, and authenticate servers and clients. Client authentication is optional.

SSL certificates use a public key encryption system that uses a matching key pair to encrypt and decrypt data. Each user creates a private key that is highly secured and not disclosed to anyone for decryption and signature. Meanwhile, the user creates a public key and discloses this key to a group of users for encryption and signature verification.

After you install an SSL certificate on a web server, HTTPS is enabled for the web server. When you access your website by using the web server, your website will transmit data over HTTPS. HTTPS helps establish trusted and encrypted connections between your website and the web server. This ensures secure transmission of data.

For more information about private keys, see [What is a public key and a private key?](/intl.en-US/Product Introduction/SSL certificate concepts/What is a public key and a private key?.md).

## HTTPS

HTTPS is based on HTTP and SSL. It is a secure version of HTTP and encrypts website communications based on SSL.

After you install an SSL certificate on the server of your website, HTTPS is enabled to activate the SSL-encrypted channel between browsers and the web server. This enables bidirectional encrypted transmission and prevents data tampering or interception during transmission.

## Nginx

NGINX is a lightweight web server and processes highly concurrent connections. You can configure it as a reverse proxy server or an email proxy server that complies with the Internet Message Access Protocol \(IMAP\) or Post Office Protocol version 3 \(POP3\). NGINX is based on BSD-like licenses. NGINX runs on different operating systems, such as Linux, Windows, FreeBSD, Solaris, AIX, and macOS. It can be used for reverse proxy, load balancing, and dynamic and static separation.

## Tengine

Tengine is a web server project initiated by Taobao. It supports all the features of NGINX and is compatible with NGINX configurations.

## PuTTY

PuTTY is connection software that supports Telnet, SSH, rlogin, raw TCP, and serial ports. It can remotely manage Linux and Windows operating systems.

## XShell

XShell is a powerful terminal emulator. It supports Telnet on SSH1 and SSH2 clients and also in Windows. XShell can remotely manage servers that run different operating systems from Windows. XShell supports VT100, VT220, VT320, Xterm, Linux, SCO ANSI, and ANSI terminal emulators and provides a variety of terminal screen views to replace traditional Telnet clients.

## CentOS

Community Enterprise Operating System \(CentOS\) is an enterprise-grade Linux distribution and is derived from the sources of Red Hat Enterprise Linux. CentOS is open source and free of charge.

## CSR

A certificate signing request \(CSR\) file contains your server and company information. When you apply for an SSL certificate, you must submit the CSR file to a CA. The CA signs the CSR file by using the private key of the root certificate and generates a public key file to issue your SSL certificate.

