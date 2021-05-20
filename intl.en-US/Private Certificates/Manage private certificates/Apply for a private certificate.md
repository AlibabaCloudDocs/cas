# Apply for a private certificate

After you create and enable a private certificate authority \(CA\) in the SSL Certificates Service console, you can apply for a private certificate by using a private intermediate CA. The private certificate can be used to authenticate identities and encrypt and decrypt data for internal applications in enterprises. This topic describes how to apply for a private certificate by using a private CA.

-   A private CA is created and enabled. For more information, see [Create a private CA](/intl.en-US/Private Certificates/Manage private CAs/Create a private CA.md) and [Enable a private CA](/intl.en-US/Private Certificates/Manage private CAs/Enable a private CA.md).
-   The **remaining service quota** of the private CA is not 0.

![Remaining service quota](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5086041261/p254745.png)

Only private intermediate CAs can be used to apply for private certificates. Private certificates are terminal entity certificates, including server certificates and client certificates. You can perform the following steps to apply for a private certificate by using a private intermediate CA.

## Procedure

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  In the left-side navigation pane, click **Private Certificates**.

3.  Find the private intermediate CA that you want to use and click **Apply for Certificate** in the Actions column.

4.  In the **Apply for Certificate** panel, configure the information about the certificate.

    ![Apply for a private certificate](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8238917161/p253401.png)

    The following table describes the related parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Certificate Type**|The type of the private certificate. Valid values:    -   **Server Certificate**: A server certificate must be installed on an application server.
    -   **Client Certificate**: A client certificate must be installed on a client browser that accesses an application.
Trusted communication can be established between the server and the client only after private certificates are separately installed on the server and the client. |
    |**Common Name \(CN\)**|The common name of the entity of the private certificate. For a server certificate, you can enter the domain name of your website or the IP address of your server. For a client certificate, you can enter a user email address or URI. |
    |**Validity Period**|The validity period of the private certificate. The validity period of the private certificate cannot exceed the service duration of the Private Certificate Authority \(PCA\) service that you purchase. For example, if the service duration of PCA that you purchase is one month, the validity period of a private certificate issued by your private CA cannot exceed 31 days. If your certificate needs a longer validity period, we recommend that you renew the PCA service to extend its service duration. For more information, see [Renew a private CA](/intl.en-US/Private Certificates/Manage private CAs/Renew a private CA.md). |
    |**SAN**|The subject alternative name \(SAN\) attribute of the private certificate. If you need to apply the certificate to multiple entities, you can add the information about other entities by using SAN attributes. For a server certificate, you can enter the domain name of your website or the IP address of your server. For a client certificate, you can enter a user email address or URI.

You can add up to 10 SAN attributes. |

5.  Click **Confirm**.

    The private certificate is immediately issued after the certificate request is submitted. To view the details about the issued private certificate, find the private certificate in the certificate list, click **Certificates** in the **Actions** column, and then view the information on the **Certificates** page.

    ![Certificate list](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2065741261/p255070.png)


## What to do next

[Export a private certificate](/intl.en-US/Private Certificates/Manage private certificates/Export a private certificate.md): You can export issued private certificates to an on-premises machine and distribute them to certificate entities for installation and use.

## References

[Revoke a private certificate](/intl.en-US/Private Certificates/Manage private certificates/Revoke a private certificate.md): Before a private certificate expires, if you no longer want to use the private certificate, you can revoke it.

