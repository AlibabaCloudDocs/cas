---
keyword: [Alibaba Cloud SSL Certificates Service, SSL certificate, refund, full refund]
---

# Refund instructions

You can request a full refund for a purchased SSL certificate when specific conditions are met. This topic describes the conditions and steps on how to request a refund in the SSL Certificates Service console.

## Refund conditions

You can request a refund for a purchased SSL certificate in the SSL Certificates Service console when specific conditions are met.

**Note:**

-   You must submit a refund request at least 15 business days before the SSL certificate expires. Otherwise, you may fail to complete the refund process and receive the refund before the SSL certificate expires.
-   If you purchased an SSL certificate by using a voucher, you cannot request a refund for the voucher.
-   If the refund for an unissued SSL certificate fails, you can continue to use the certificate.
-   You cannot request a refund for a free DV SSL certificate no matter whether it is valid.

The following table describes specific conditions for refunds.

|Whether an SSL certificate is issued|Duration|Whether the SSL certificate is submitted for validation|Refund|Refund amount|Remarks|
|------------------------------------|--------|-------------------------------------------------------|------|-------------|-------|
|Unissued|No more than 5 calendar days after purchase|**Not submitted** or submitted but **not validated**|Supported|Full refund|Manual validation is not required. You can immediately receive the refund after you submit the refund request.|
|Unissued|More than 5 calendar days after purchase to 15 calendar days before expiration|**Not submitted** or submitted but **not validated**|Supported|Full refund|Manual validation is required. The validation process requires up to 15 business days, but it is usually completed within 5 business days. You can immediately receive the refund after validation. For more information about how to view the expiration time of an SSL certificate, see [What to do next](#section_tgl_wo3_23d).|
|Unissued|Within 15 calendar days before expiration|No matter whether the SSL certificate is validated|Not supported|None|If you submit a refund request within 15 business days before the SSL certificate expires, the request may not be validated before the expiration, and therefore the refund fails.|
|Issued|Revocation completed within 28 calendar days after issuance|Validated|Supported|Full refund|Manual validation is required. The validation process requires up to 15 business days, but it is usually completed within 5 business days. You can immediately receive the refund after validation.|
|Issued \(more than 28 calendar days after issuance\)|Not expired|Validated|Not supported|None|None|
|Issued or unissued|Expired|No matter whether the SSL certificate is validated|Not supported|None|None|

In the certificate list, you can filter SSL certificates in the **Issued** state. Then, find an SSL certificate and click **Details** in the **Operate** column. In the **Certificate Details** panel, you can view the date when the SSL certificate was issued.

![Date when the SSL certificate was issued](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2592178061/p136003.png)

## Refund procedure

1.  On the Overview page, find the SSL certificate for which you want to request a refund, and click **Refund**.

    ![Refunds](../images/p149195.png)

    **Note:** You can find the SSL certificate in the certificate list. If an SSL certificate is in the **Issued** state and has been issued for more than 30 calendar days, the system does not display the **Refund** button for this certificate.

2.  In the Refund Application panel, specify **Refund Reasons**.

    The following reasons are supported.

    |Reason|Operation|
    |------|---------|
    |**I failed to apply for or install the certificate, and do not know where to get help.**|Click **Next** to determine whether to seek technical support. If you require technical support, enter your DingTalk information or mobile number in the Refund Application panel. Alibaba Cloud technical support will contact you in a timely manner.**Note:** Make sure that the DingTalk information and mobile number you enter are valid. |
    |**The certificate application process is stuck in the Verifying or Verification Failed state. This affects my business.**|Click **Next** to determine whether to seek technical support. If you require technical support, enter your DingTalk information or mobile number in the Refund Application panel. Alibaba Cloud technical support will contact you in a timely manner.**Note:** Make sure that the DingTalk information and mobile number you enter are valid. |
    |**The type of the renewed certificate is inconsistent with that of the original certificate. I want to claim a refund and purchase a new certificate.**|Go to Step 4.|
    |**I no longer need the certificate.**|Go to Step 4.|
    |**Other**|Enter your feedback or suggestions.|

3.  Click **OK**.

    After you submit the refund request, the state of the SSL certificate on the Overview page in the SSL Certificates Service console changes to **Validating Application**.

    **Note:** The validation process requires up to 15 business days, but it is usually completed within 5 business days. The refund is returned to the Alipay account, online bank account, or Alibaba Cloud account that you used to pay for the purchase order.

    After you submit a refund request, you can cancel the refund request, view the refund progress, or check the validity period of the SSL certificate. For more information, see [What to do next](#section_tgl_wo3_23d).


## What to do next

-   **Cancel a refund request**

    If you want to cancel a refund request, find the SSL certificate on the Overview page and click **Cancel refund**.

    **Note:** You can cancel the refund request only for an SSL certificate in the **Validating Application** state.

-   **View the refund progress**

    If you want to view the refund progress, filter the SSL certificates in the Refunded state in the SSL Certificates Service console. If the refund request is rejected, the system provides further details.

-   **Check the validity period of an SSL certificate**
    -   **Issued**

        If the SSL certificate is issued, filter SSL certificates in the **Issued** state in the certificate list. Then, find the SSL certificate and check the value of **Expire On**.

        ![Certificate validity period](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9782027951/p101277.png)

    -   **Unissued**

        The validity period of an SSL certificate starts from the date when the certificate was issued. If an SSL certificate is not issued, it does not expire. In this case, the SSL certificate is in a state other than **Issued**, such as in the **Paid** or **Validating Application** state.


## References

[Billing](/intl.en-US/Product Pricing/Billing.md)

