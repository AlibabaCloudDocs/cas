# Create a private CA

SSL Certificates Service supports Private Certificate Authority \(PCA\). PCA allows you to create a private certificate authority \(CA\) for your enterprise at low costs. This way, you do not need to create or maintain public key infrastructure \(PKI\). This topic describes how to create a private CA in the SSL Certificates Service console. After you create a private CA, PCA is enabled.

Private CAs are classified into private root CAs and private intermediate CAs. A private intermediate CA is subordinate to a private root CA. A private root CA may include one or more private intermediate CAs. Only private intermediate CAs can issue private certificates, including server certificates and client certificates.

If you create a private CA for the first time, you must first create a private root CA. After you create a private root CA, you can obtain one private root CA and one private intermediate CA. By default, the private intermediate CA has the quota to issue 10 private certificates.

You can create more private intermediate CAs for the existing private root CA based on the organizational structure of your enterprise. For example, you can use the private root CA to create private intermediate CAs for different departments of your enterprise. You can also purchase the quota for private certificates to issue more private certificates by using the existing private intermediate CA.

## Create a private root CA

If you create a private CA for the first time, perform the following operations to first create a private root CA:

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  In the left-side navigation pane, click **Private Certificates**.

3.  In the upper-left corner of the **Private Certificates** page, click **Purchase Private Root CA**.

4.  In the **Purchase Private Root CA** panel, configure the parameters.

    ![Purchase Private Root CA](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7276041261/p253396.png)

    The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Commodity Module**|**Certificate Service** is automatically selected. This option allows you to create a private CA for your enterprise to maintain and manage certificates.|
    |**Intended Use**|**Internal Use in Enterprise \(Without Regulatory Requirements\)** is automatically selected. PCA is suitable for enterprises that require encrypted communication between its internal systems to implement identity authentication and secure transmission of application data. The internal systems include office automation \(OA\) and human resources \(HR\) systems. PCA is not used to meet regulatory requirements and industry specifications.|
    |**Product specifications**|**Create a root CA** is automatically selected.|
    |**Certificate Algorithm**|The type of algorithm that is used by the certificates issued by the private CA . Valid values: **RSA**, **SM Algorithms \(Commercial Cryptographic Algorithms of China\)**, and **ECC**. |
    |**Subscription Duration**|The subscription duration of the private CA. The minimum value is **1 Month**. **Note:**

    -   You can use a private CA to issue private certificates within the subscription period of the private CA. After the private CA expires, you cannot use the private CA to issue private certificates even if the quota to issue private certificates is not used up.
    -   The validity period of private certificates issued by the private CA cannot exceed the subscription period of the private CA. For example, if you set Subscription Duration to 1 Month, the validity period of private certificates issued by the private CA cannot exceed 30 days. |

5.  Click **Buy Now**.

6.  Confirm your order and complete the payment.

    After you complete the payment, you can view the newly created private CA on the **Private Certificates** page in the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas). After you create a private root CA, you can obtain one private root CA and one private intermediate CA. By default, both the private root CA and the private intermediate CA are in the **Disabled** state.

    ![Private CA](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7276041261/p253440.png)


## What to do next

After you create a private CA, you must enable the private CA before you can use it to issue private certificates. For more information about how to enable a private CA, see [Enable a private CA](/intl.en-US/Private Certificates/Manage private CAs/Enable a private CA.md).

## Related operations

-   **Create a private intermediate CA**: After you create and enable a private root CA, you can create multiple private intermediate CAs for this private root CA.

    **Note:**

    -   By default, a private intermediate CA created for the existing private root CA does not have the quota to issue private certificates. You cannot use this private intermediate CA to issue private certificates. After you create a private intermediate CA for the existing private root CA, you must purchase the required quota before you can use the private intermediate CA to issue private certificates.
    -   When you create a private intermediate CA for the existing private root CA, the value of the **Certificate Algorithm** parameter for the private intermediate CA is automatically set to that for the private root CA. You cannot modify this parameter.
    Procedure: In the private CA list, find the private root CA that is in the **Enabled** state and click **Create CA** in the **Actions** column. On the page that appears, configure the parameters and complete the payment as prompted.

    ![Create CA](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7276041261/p265997.png)

-   **Purchase the quota to issue private certificates**: If an existing private intermediate CA does not have the sufficient quota to issue the required number of private certificates, you can purchase extra quotas. This way, you can use the private intermediate CA to issue more private certificates.

    Procedure: In the private CA list, find the private intermediate CA for which you want to purchase the quota to issue private certificates and click **Purchase Certificate** in the **Actions** column. On the page that appears, complete the payment as prompted.

    ![Purchase the quota to issue private certificates](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8276041261/p266004.png)

-   [Claim a refund](/intl.en-US/Private Certificates/Manage private CAs/Claim a refund.md): You can request a refund for a private CA that is in the Disabled state. If the private CA is enabled, you cannot request a refund.
-   [Renew a private CA](/intl.en-US/Private Certificates/Manage private CAs/Renew a private CA.md): After a private CA expires, you cannot use the private CA to issue private certificates. You can renew the private CA to continue to use it.

