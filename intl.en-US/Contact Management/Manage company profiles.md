# Manage company profiles

When you submit an application for an Organization Validation \(OV\) or Extended Validation \(EV\) certificate, you must provide company information such as the business license for the CA to validate. After you create a company profile, SSL Certificates Service automatically saves the company information for later use. This topic describes how to create, edit, and delete a company profile.

## Create a company profile

You can create a company profile by using one of the following methods:

-   Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas) and open the **Information Management** page. Then, click Create Company Profile on the **Company** tab. The following procedure is based on this method.
-   When you submit a certificate application, select **Create Company Profile** from the **Company** drop-down list. If you use this method, the system automatically saves the company information that you enter to the **Company** tab of the **Information Management** page. You do not need to enter the information again the next time you submit a certificate application.

**Procedure**

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  In the left-side navigation pane, click **Information Management**.

3.  Click the **Company** tab.

4.  On the **Company** tab, click **Create Company Profile**.

5.  In the **Create Company Profile** dialog box, configure the parameters based on your business requirements.

    ![Company information](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6378971161/p210361.png)

    **Note:** Make sure that the company information you enter is true and valid. The CA examines the company information when they validate your certificate application.

    |Parameter|Description|
    |---------|-----------|
    |**Company Name**|The name of the company that owns the domain name bound to your certificate.|
    |**Company Type**|The registration type of the company. Valid values: **Private Enterprise/Self-employed**, **Business Enterprise**, **Government Entity**, and **Non-Profit Organization**.|
    |**Company Phone**|The phone number of the company.|
    |**Organization Code**|The organization code of the company.|
    |**Company Region**|The region where the company is located.|
    |**Detailed Address**|The detailed address of the company.|
    |**Postal Code**|The postal code of the company.|
    |**Business License**|A photo of the company license. You can click the ![Add](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4532455161/p210626.png) icon to upload a photo of your business license. Both JPG and PNG formats are supported.|

6.  Click **OK**.

    After you create a company profile, you can view it on the **Company** tab in the contact list and click **Edit** or **Delete** to manage the profile based on your business requirements.

    ![Company](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7378971161/p210360.png)


## What to do next

When you submit a certificate application, you can select an existing company profile from the **Company** drop-down list. For more information, see [Apply for a certificate](/intl.en-US/Issue Certificates/Apply for a certificate.md). When the CA validates your certificate application, they examine the company profile that you select.

