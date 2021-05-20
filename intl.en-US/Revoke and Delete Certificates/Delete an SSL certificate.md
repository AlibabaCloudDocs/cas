# Delete an SSL certificate

In the SSL Certificates Service console, you can delete expired and revoked SSL certificates from the certificate list. This topic describes how to delete an SSL certificate.

-   The SSL certificate that you want to delete is no longer valid or is revoked.

    You can delete an expired SSL certificate from the certificate list in the SSL Certificates Service console at any time.

    If you want to delete an SSL certificate before it expires, you must revoke it first. Then, you can delete the certificate from the certificate list in the SSL Certificates Service console. If you revoke an issued SSL certificate, the SSL certificate is deregistered from the certificate authority \(CA\) that issues it. After the certificate is revoked, the certificate cannot be used for encryption and is no longer trusted by your browser. For more information, see [Revoke certificates](/intl.en-US/Revoke and Delete Certificates/Revoke certificates.md).

    **Note:** If you manually upload a third-party SSL certificate to the SSL Certificates Service console for management, you can delete the certificate from the console at any time.

-   The SSL certificate that you want to delete is not deployed to an Alibaba Cloud service.

    **Warning:** If you delete an SSL certificate but are not sure whether it is deployed to an Alibaba Cloud service, the deletion may cause service interruptions.


## Procedure

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  On the **Overview** page, select **Expired** or **Revoked** from the status drop-down list above the certificate list.

3.  Find the certificate that you want to delete and click **Delete** in the Actions column.

4.  In the **Confirmation** message, click **Delete**.

    ![Confirm deletion](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8175741261/p263622.png)

    After the certificate is deleted, it is permanently removed from the certificate list.


