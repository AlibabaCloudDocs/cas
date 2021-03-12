# Authorize SSL Certificates Service before using the Website Security module

When you access the Website Security page of the SSL Certificates Service console for the first time, you must authorize SSL Certificates Service to access your website assets. This topic describes how to authorize SSL Certificates Service to access your website assets.

The authorization is required only when you access the **Website Security** page for the first time. After the authorization is completed, you can access the page at all times.

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  In the left-side navigation pane, click **Website Security Check**.

3.  Select **Authorize** and click **Enabled**.

    **Note:** If SSL Certificates Service has been authorized to access your website assets, the status of all SSL certificates on your websites is automatically displayed on the **Website Security** page. For more information, see [View the status of SSL certificates](/intl.en-US/Website Security Check/View the status of SSL certificates.md).

    ![Authorization for first use](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6502239061/p100429.png)

4.  On the **Cloud Resource Access Authorization** page, click **Confirm Authorization Policy**.

    ![Cloud Resource Access Authorization](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5336050161/p207282.png)


After the authorization is completed, you can log on to the [RAM console](https://ram.console.aliyun.com/roles) and navigate to the **RAM Roles** page. Then, you can view the **AliyunCASDefaultRole** role created for SSL Certificates Service. SSL Certificates Service uses this role to access your resources in cloud services and detect your website assets.

![AliyunCASDefaultRole](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5336050161/p207283.png)

You can click the role name to view the permissions that are granted to the role. For more information, see [Policy overview](/intl.en-US/Policy Management/Policy overview.md).

[View the status of SSL certificates](/intl.en-US/Website Security Check/View the status of SSL certificates.md)

