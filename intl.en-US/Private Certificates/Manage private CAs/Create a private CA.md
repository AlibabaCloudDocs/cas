# Create a private CA

SSL Certificates Service provides the Private Certificate Authority \(PCA\) service. This service allows you to create private certificate authorities \(CAs\) for your enterprise at low costs without the need to build and maintain public key infrastructure \(PKI\). This topic describes how to create a private CA in the SSL Certificates Service console. The operation to create a private CA is the operation to purchase the PCA service.

Private CAs are divided into private root CAs and private intermediate CAs. A private intermediate CA is subordinate to a private root CA. A private root CA contains one or more private intermediate CAs. Only private intermediate CAs can issue private certificates, such as server certificates and client certificates.

If you have not created a private CA, you must first create a private root CA. After a private root CA is created, you obtain a private intermediate CA in addition to the private root CA. By default, the private intermediate CA can issue 10 certificates.

You can continue to create multiple private intermediate CAs under the existing private root CA based on the organizational framework of your enterprise. For example, you can create private intermediate CAs for different departments in your enterprise. Alternatively, you can purchase certificates for the existing private intermediate CA to increase the number of certificates that this intermediate CA can issue.

## Create a private root CA

If you have not created a private CA, you must first create a private root CA by performing the following operations:

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  In the left-side navigation pane, click **Private Certificates**.

3.  On the **Private Certificates** page, click **Purchase Private Root CA** above the private CA list.

4.  In the **Purchase Private Root CA** panel, set the parameters.

    ![Purchase a private root CA](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7276041261/p253396.png)

    The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Commodity Module**|By default, **Certificate Service** is selected. This means that you can purchase the PCA service for your enterprise to maintain and manage certificates.|
    |**Intended Use**|**Internal Use in Enterprise \(Without Regulatory Requirements\)**: This option is selected by default. PCA is used for network communication that requires cryptographic technology among internal systems of an enterprise, such as the office automation \(OA\) and human resources \(HR\) systems. PCA enables user authentication and secure transmission of application data. PCA is not used to meet regulatory and industry specifications.|
    |**Product Specifications**|By default, **Create Root CA** is selected.|
    |**Certificate Algorithm**|Select a type of certificate algorithm that the private CA uses when it issues certificates. Valid values: **RSA**, **Chinese Cryptographic Algorithm \(SM\)**, and **ECC**. |
    |**Subscription Duration**|Select a duration for the service to be purchased. The minimum value is **1 Month**. **Note:**

    -   You can apply for certificates from a private CA within the duration of the PCA service that you purchase. After the PCA service expires, the private CA cannot issue certificates even if the number of remaining certificates that the private CA can issue is not 0.
    -   The validity period of a private certificate issued by a private CA cannot exceed the duration of the PCA service that you purchase. For example, if the duration of the PCA service that you purchase is one month, the validity period of a private certificate issued by the private CA cannot exceed 31 days. |

5.  Click **Buy Now**.

6.  Confirm your order and complete the payment.

    After you complete the payment, you can view the new private CA on the **Private Certificates** page in the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas). After a private root CA is created, you obtain a private intermediate CA in addition to the private root CA. By default, the values of **Status** of the private root CA and private intermediate CA are **Disabled**.

    ![Private CA](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7276041261/p253440.png)


## What to do next

After you create a private CA, you must enable the private CA so that it can issue private certificates. For more information about how to enable a private CA, see [Enable a private CA](/intl.en-US/Private Certificates/Manage private CAs/Enable a private CA.md).

## Related operations

-   **Create a private intermediate CA**: After you create and enable a private root CA, you can continue to create multiple private intermediate CAs under this private root CA.

    Notes:

    -   By default, a private intermediate CA that you create under the existing private root CA does not contain certificate resources. This means that the number of certificates that the private intermediate CA can issue is 0. You must purchase certificates for the private intermediate CA after you create it.
    -   When you create a private intermediate CA under the existing private root CA, the **certificate algorithm** of the private intermediate CA is the same as that of the private root CA by default and cannot be changed.
    In the private CA list, find the private root CA that is the **Enabled** state and under which you want to create a private intermediate CA, and click **Create CA** in the **Actions** column. Then, complete the purchase by following the instructions on the page that appears.

    ![Create a private intermediate CA](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7276041261/p265997.png)

-   **Purchase certificates**: If the number of certificates that the existing private intermediate CA contains cannot meet your requirements, you can purchase certificates under this private intermediate CA to increase the number of certificates that it can issue.

    In the private CA list, find the private intermediate CA for which you want to purchase certificates, and click **Purchase Certificate** in the **Actions** column. Then, complete the purchase by following the instructions on the page that appears.

    ![Purchase certificates](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8276041261/p266004.png)

-   [Claim a refund](/intl.en-US/Private Certificates/Manage private CAs/Claim a refund.md): You can claim a refund for a private CA that is in the Disabled state. If the private CA is enabled, you cannot claim a refund for the private CA.
-   [Renew a private CA](/intl.en-US/Private Certificates/Manage private CAs/Renew a private CA.md): A private CA cannot issue certificates after the PCA service expires. You can renew the PCA service to extend its service duration.

