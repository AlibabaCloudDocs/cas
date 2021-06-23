# Billing

This topic describes the billing and pricing of SSL Certificates Service features, including the certificate, website HTTP proxy, and Private Certificate Authority \(PCA\) features.

## Certificate

The prices of certificates vary based on types and brands. For more information about certificate prices, see [SSL Certificates Service buy page](https://common-buy-intl.aliyun.com/?commodityCode=cas_intl#/buy).

## PCA

SSL Certificates Service supports PCA. PCA allows you to build a private certificate authority \(CA\) for your enterprise. Then, you can issue and manage self-signed private certificates within your enterprise. For more information about PCA, see [Overview](/intl.en-US/Private Certificates/Overview.md).

PCA fees are charged on a **subscription** basis. You can set the subscription duration to one month, two months, three months, four months, five months, six months, one year, or two years. Private CAs are classified into private root CAs and private intermediate CAs and is billed on a subscription basis. After you purchase a private CA, you can use the private CA to issue private certificates during the validity period of the private CA. By default, you can use a private CA to issue a specific number of private certificates free of charge. If you want to use the private CA to issue more private certificates, you must purchase additional private certificate quota.

A private CA supports different types of algorithms. The prices of a private CA and a private certificate vary based on algorithms. The following list describes the pricing details:

-   **Private root CA**: consists of 1 private root CA, 1 private intermediate CA, and the quota for 10 private certificates by default.

    **Note:** If you enable PCA for the first time, you must purchase a private root CA. For more information, see [Create a private root CA](/intl.en-US/Private Certificates/Manage private CAs/Create a private CA.md).

    |Algorithm|Price \(USD/month\)|
    |---------|-------------------|
    |RSA|760|
    |SM|1,000|
    |ECC|800|

-   **Private intermediate CA**: consists of only one private intermediate CA.

    **Note:** By default, a private root CA contains one private intermediate CA. If you want to create multiple private intermediate CAs under the private root CA, you must separately purchase private intermediate CAs. For more information, see [Create a private intermediate CA](/intl.en-US/Private Certificates/Manage private CAs/Create a private CA.md). A separately purchased intermediate CA does not contain the quota for private certificates. After you purchase a private intermediate CA, you must purchase a specific quota for private certificates. Then, you can use the private intermediate CA to issue private certificates.

    |Algorithm|Price \(USD/month\)|
    |---------|-------------------|
    |RSA|380|
    |SM|500|
    |ECC|400|

-   **Private certificate**

    **Note:** If you want to issue more private certificates by using a private CA, you must purchase the quota for private certificates. For more information, see [Purchase the quota for private certificates](/intl.en-US/Private Certificates/Manage private CAs/Create a private CA.md).

    |Algorithm|Price for every 10 private certificates \(USD\)|
    |---------|-----------------------------------------------|
    |RSA|7|
    |SM|8.5|
    |ECC|7.5|


## Expiration

If your purchased certificates or value-added services expire, they automatically stop. Take note of the following points:

-   Seven days before your certificates or value-added services expire, the system sends you emails or text messages that prompt you to renew the certificates or value-added services at the earliest opportunity. If you do not renew the certificates or value-added services before they expire, your website can no longer provide HTTPS-encrypted data transmission.
-   After your certificates or value-added services expire, the system retains the settings of your certificates and value-added services for seven days. If you renew the certificates or value-added services within seven days after they expire, you can use the original settings. If you do not renew the certificates or value-added services within seven days after they expire, the settings are cleared. In this case, you must purchase certificates or value-added services and configure the settings again.

## References

-   [Purchase an SSL Certificates Service instance](/intl.en-US/Buy Certificates/Purchase an SSL Certificates Service instance.md)
-   [Why is "Failed to activate" returned when I purchase a certificate?]()
-   [Request a refund for an SSL certificate](/intl.en-US/Refund/Request a refund for an SSL certificate.md)
-   [Manually renew an SSL certificate](/intl.en-US/Renew Certificates/Manually renew an SSL certificate.md)
-   [What should I do when my SSL certificate expires?]()

