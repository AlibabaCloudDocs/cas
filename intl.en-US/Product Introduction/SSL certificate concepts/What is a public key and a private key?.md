---
keyword: [certificate, SSL, private key, asymmetric encryption]
---

# What is a public key and a private key?

A public key and a private key are a key pair that is obtained by using an encryption algorithm. The public key and private key are used for asymmetric encryption. The public key is used to encrypt sessions and verify digital signatures, whereas the matching private key is used to decrypt the session data to ensure secure data transmission. The public key is the public part of a key pair, whereas the private key is the private part managed by users.

A key pair that is generated by using an encryption algorithm is unique worldwide. If you use a key in a key pair to encrypt a piece of data, the data can be decrypted only by using the other key in this key pair. For example, data encrypted with a public key must be decrypted with the matching private key. Data encrypted with a private key must be decrypted with the matching public key.

## How does an SSL certificate work?

An SSL certificate adopts a public-key encryption system that uses a matching key pair to encrypt and decrypt data. Each user creates a private key that is highly secured and not disclosed to anyone for decryption and signature. The user also creates a public key and discloses this key to a group of users for encryption and signature verification.

Only the key owner can use the matching private key to encrypt a document, and therefore generate a digital signature.

An SSL certificate is a document digitally signed by a certificate authority \(CA\). This document contains information about a public key and the owner of the public key. A certificate must contain a public key, a certificate name, and a digital signature of the corresponding CA. Digital certificates are valid for only a specific period of time.

For more information about private keys, see [How does SSL Certificates Service protect private keys?](/intl.en-US/Product Introduction/SSL certificate concepts/How does SSL Certificates Service protect private keys?.md).

## Create a private key

SSL Certificates Service has the following requirements for the private key length and the encryption algorithm that is used to generate a private key:

-   The Rivest-Shamir-Adleman \(RSA\) algorithm is used.
-   The private key length must be at least 2,048 bits.

You can use one of the following methods to create your private key:

-   **Use OpenSSL to generate a private key**
    1.  You can download the latest OpenSSL installation package from the [OpenSSL official website](http://www.openssl.org/source/).

        **Note:** The version of OpenSSL must be 1.0.1g or later.

    2.  After OpenSSL is installed, run the `openssl genrsa -out myprivate.pem 2048` command on the command line to generate your private key file. myprivate.pem is the generated private key file. 2,048 represents the private key length.
-   **Use Keytool to generate and export a private key**

    Keytool is a key management tool installed with JDK. This tool can create keystore files in JKS format for SSL certificates. You can obtain Keytool when you download JDK from [the official website](http://www.oracle.com/technetwork/java/javase/downloads/index.html).

    By default, the public key and private key that are created by using Keytool are not exported. You must export the private key from a .keystore file that has been created. For more information about how to export a private key from a .keystore file, see [Certificate format conversion](/intl.en-US/Product Introduction/SSL certificate concepts/What formats are used for mainstream digital certificates?.md).

    In the exported file, your private key is visible if a section of the file is similar to one of the following examples:

    ```
    
    -----BEGIN RSA PRIVATE KEY-----
    ......
    -----END RSA PRIVATE KEY-----
    ```

    or

    ```
    
    -----BEGIN PRIVATE KEY-----
    ......
    -----END PRIVATE KEY-----
    ```

    **Note:** We recommend that you keep your private key confidential. If the private key is lost or becomes corrupt, you cannot use the matching public key or digital certificate that you have requested.

