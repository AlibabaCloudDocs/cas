# Enable a private CA

After you create a private certificate authority \(CA\), you must enable the private CA so that it can issue private certificates. This topic describes how to enable a private CA.

A private CA is created. For more information, see [Create a private CA](/intl.en-US/Private Certificates/Manage private CAs/Create a private CA.md).

**Note:** Refunds are not provided after a private CA is enabled. For more information, see [Claim a refund](/intl.en-US/Private Certificates/Manage private CAs/Claim a refund.md).

## Step 1: Enable a private root CA

If you enable a private CA for the first time, you must enable the private root CA and then enable the private intermediate CA. If the private root CA is enabled, you can enable the private intermediate CA that is subordinate to the private root CA.

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  In the left-side navigation pane, click **Private Certificates**.

3.  On the **Private Certificates** page, find the private root CA that you want to enable and click **Enable** in the **Actions** column. You can enable a private root CA only when it is in the **Disabled** state.

4.  In the **CA Information** panel, configure the information about the private root CA.

    ![Enable a CA](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8477917161/p253399.png)

    The following table describes the related parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Organization \(O\)**|The name of the organization that you want to associate with the private CA. Example: Alibaba Cloud Computing Co., Ltd. |
    |**Organizational Unit \(OU\)**|The name of the organizational unit that you want to associate with the private CA. Example: IT department |
    |**Common Name \(CN\)**|The common name or abbreviation of the organization that you want to associate with the private CA. Example: Alibaba Cloud |
    |**Country/Region \(C\)**|The country or region where the organization is located. Example: China |
    |**Province \(S\)**|The province where the organization is located. Example: Zhejiang |
    |**City \(L\)**|The city where the organization is located. Example: Hangzhou |
    |**Private Key Algorithm**|The private key algorithm that the private CA uses. Supported private key algorithms vary based on the value of **Certificate Algorithm** that you select when you purchase the Private Certificate Authority \(PCA\) service. The following rules describe supported private key algorithms for different certificate algorithms that the private CA uses:

    -   If the certificate algorithm is **RSA**, private key algorithms such as **RSA\_1024**, **RSA\_2048**, and **RSA\_4096** are available.
    -   If the certificate algorithm is **SM \(Chinese Cryptographic Algorithm\)**, private key algorithms such as **SM2\_256**, **SM2\_384**, and **SM2\_512** are available.
    -   If the certificate algorithm is **ECC**, private key algorithms such as **ECC\_256**, **ECC\_384**, and **ECC\_512** are available. |
    |**Validity Period**|The validity period of the private CA. Valid values: **5Year\(s\)**, **10Year\(s\)**, **15Year\(s\)**, and **20Year\(s\)**.|

5.  Click **Confirm and Enable**.

6.  In the **Note** message, click **OK**.

    ![Note](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1636041261/p266061.png)

    After you enable the private root CA, the value in the Status column for the private root CA changes to **Enabled**.


## Step 2: Enable a private intermediate CA

You can enable a private intermediate CA that is subordinate to a private root CA only after the private root CA is enabled.

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  In the left-side navigation pane, click **Private Certificates**.

3.  On the **Private Certificates** page, find the private intermediate CA that you want to enable and click **Enable** in the **Actions** column. You can enable a private intermediate CA only when it is in the **Disabled** state.

    **Note:** If the private root CA to which a private intermediate CA is subordinate is disabled, you cannot enable the private intermediate CA.

4.  In the **CA Information** panel, configure the information about the private intermediate CA.

    ![Enable a CA](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8477917161/p253399.png)

    The following table describes the related parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Organization \(O\)**|The name of the organization that you want to associate with the private CA. Example: Alibaba Cloud Computing Co., Ltd. |
    |**Organizational Unit \(OU\)**|The name of the organizational unit that you want to associate with the private CA. Example: IT department |
    |**Common Name \(CN\)**|The common name or abbreviation of the organization that you want to associate with the private CA. Example: Alibaba Cloud |
    |**Country/Region \(C\)**|The country or region where the organization is located. Example: China |
    |**Province \(S\)**|The province where the organization is located. Example: Zhejiang |
    |**City \(L\)**|The city where the organization is located. Example: Hangzhou |
    |**Private Key Algorithm**|The private key algorithm that the private CA uses. Supported private key algorithms vary based on the value of **Certificate Algorithm** that you select when you purchase the Private Certificate Authority \(PCA\) service. The following rules describe supported private key algorithms for different certificate algorithms that the private CA uses:

    -   If the certificate algorithm is **RSA**, private key algorithms such as **RSA\_1024**, **RSA\_2048**, and **RSA\_4096** are available.
    -   If the certificate algorithm is **SM \(Chinese Cryptographic Algorithm\)**, private key algorithms such as **SM2\_256**, **SM2\_384**, and **SM2\_512** are available.
    -   If the certificate algorithm is **ECC**, private key algorithms such as **ECC\_256**, **ECC\_384**, and **ECC\_512** are available. |
    |**Validity Period**|The validity period of the private CA. Valid values: **5Year\(s\)**, **10Year\(s\)**, **15Year\(s\)**, and **20Year\(s\)**.|

5.  Click **Confirm and Enable**.

6.  In the **Note** message, click **OK**.

    ![Note](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1636041261/p266061.png)

    After you enable your private intermediate CA, the value in the Status column for the private intermediate CA changes to **Enabled**.


## What to do next

[Apply for a private certificate](/intl.en-US/Private Certificates/Manage private certificates/Apply for a private certificate.md): After you enable a private root CA and its private intermediate CA, you can apply for a private certificate from the enabled private intermediate CA.

## References

[Revoke a private CA](/intl.en-US/Private Certificates/Manage private CAs/Revoke a private CA.md): Before a private CA expires, if you no longer want to use the private CA, you can revoke it.

