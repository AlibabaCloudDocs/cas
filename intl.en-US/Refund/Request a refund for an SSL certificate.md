# Request a refund for an SSL certificate

You can request a full refund for an SSL certificate purchased in the SSL Certificates console if the certificate meets specific conditions. This topic describes the conditions and steps on how to request a refund in the SSL Certificates Service console.

## Refund conditions

You can request a refund for an SSL certificate purchased in the SSL Certificates Service console if the certificate meets specific conditions.

**Note:**

-   You must submit a refund request at least 15 business days before the SSL certificate expires. Otherwise, you may fail to complete the refund process and receive the refund before the SSL certificate expires.
-   If you purchased an SSL certificate by using a voucher, you cannot request a refund for the voucher. You can request a refund only for the amount that you actually paid.
-   If the refund for an unissued SSL certificate fails, you can continue to use the certificate.
-   You cannot request a refund for a free Domain Validation \(DV\) SSL certificate no matter whether the certificate is valid.

The following table describes specific refund conditions.

|Issuance|Duration|Validation|Refund|Refund amount|Remarks|
|--------|--------|----------|------|-------------|-------|
|Unissued|No more than five calendar days after purchase|**Not submitted for validation** or submitted but **not validated**|Supported|Full refund|Manual validation is not required. You can immediately receive the refund after you submit the refund request.|
|Unissued|More than 5 calendar days after purchase to 15 calendar days before expiration|**Not submitted for validation** or submitted but **not validated**|Supported|Full refund|Manual validation is required. The validation process takes up to 15 business days, but is completed within 5 business days on average. You can immediately receive the refund after validation.|
|Unissued|Less than 15 calendar days before expiration|No matter whether the SSL certificate is validated|Not supported|None|If you submit a refund request within less than 15 business days before the SSL certificate expires, the request may not be validated before the expiration. As a result, the refund fails.|
|Issued|Revocation completed within 28 calendar days after issuance|Validated|Supported|Full refund|Manual validation is required. The validation process takes up to 15 business days, but is completed within 5 business days on average. You can immediately receive the refund after validation.|
|Issued for more than 28 calendar days|Unexpired|Validated|Not supported|None|None.|
|Issued or unissued|Expired|No matter whether the SSL certificate is validated|Not supported|None|None.|

## Procedure

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  On the **Overview** page, find the SSL certificate for which you want to request a refund, and click **Refund** in the **Actions** column.

    **Note:** You can find the SSL certificate in the certificate list. If an SSL certificate is in the **Issued** state and has been issued for more than 28 calendar days, the **Refund** button does not appear for this certificate.

3.  In the **Refund Application** panel, select an option for **Refund Reasons** and click **Next**.

    ![Refund request](../images/p263799.png)

    After you submit the refund request, wait for the validation.

    The validation process takes up to 15 business days, but is completed within 5 business days on average. The refund is returned to the Alipay account, online bank account, or Alibaba Cloud account that you used to pay for the purchase order.

    To cancel the refund after you submit a refund request, find the certificate on the **Overview** page and click **Cancel Refund** in the **Actions** column.


