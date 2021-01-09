# Install SSL certificates in IIS servers

This topic describes how to install a downloaded Alibaba Cloud SSL certificate in an \(Internet Information Services\) IIS server.

## Prerequisites

You selected **Automatic** for CSR Generation when applying for the certificate.

If you selected **Manual** for CSR Generation when applying for the certificate, no certificate file is generated. You have to download the .crt certificate whose Server Type is **Other**, and then run the OpenSSL command to convert the certificate to .pfx format.

## Procedure

1.  Log on to the [Alibaba Cloud SSL Certificates console](https://yundunnext.console.aliyun.com/?p=casnext#/overview/cn-hangzhou).
2.  Log on to the Alibaba Cloud SSL Certificates console.
3.  On the **SSL Certificates** page, locate the target SSL certificate and click **Download** in the lower-right corner.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9199797851/p33499.png)

4.  In the **Download Certificate** dialog box, locate the row that contains the certificate whose Server Type is IIS, and click **Download** in the **Actions** column to download the package to your local host.
5.  Decompress the package. You will obtain a certificate file \(suffixed with .pfx or of .pfx file format\) and a key file \(suffixed with .txt or of .txt file format\).

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255633691_en-US.png)

    **Note:** Each time the certificate is downloaded, a new password is generated, which is valid only for the current certificate. To update the certificate file, you also need to update the matching key file.

6.  In the **Console** of your operating system, import your IIS server certificate file.
    1.  Choose **Start** \> **Run** \> **MMC** to open the console.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255633701_en-US.png)

    2.  Choose **File** \> **Add/Remove Snap-in**.****

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255633702_en-US.png)

    3.  In the **Add or Remove Snap-ins** dialog box, choose **Certificates** \> **Add** \> **Computer account** \> **Next** \> **Local computer: \(the computer this console is running on\)** \> **Finish**.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255633703_en-US.png)

    4.  In the left-side navigation pane of the console, click **Certificates** under **Console Root** to expand the certificate list.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255633705_en-US.png)

    5.  Choose **Personal** \> **All Tasks** \> **Import**.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255633706_en-US.png)

    6.  In the Certificate Import Wizard dialog box, click **Browse**. In the Open dialog box, select the downloaded .pfx certificate file and click Open to import it.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255633837_en-US.png)

        **Note:** In the Open dialog box, select **All Files \(\*.\*\)** from the file type drop-down list on the right of **File Name**.

    7.  Enter the password in the key file.

        You can open the **pfx-password .txt** file in the downloaded IIS server certificate files to retrieve the password.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255633838_en-US.png)

    8.  Select **Automatically select the certificate store based on the type of certificate** and click **Next** to complete the import.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255733839_en-US.png)

7.  Assign a certificate for the server.
    1.  Go to the IIS8.0 manager, locate the website where the certificate is to be deployed, and click **Bind**.
    2.  In the **Site Bindings** dialog box, choose **Add** \> **https** \> **443** \> **SSL certificate** \> **OK**.

        **Note:** The default port for SSL is port 443, and we recommend this not be changed. If other ports are used, such as 8443, enter `https://www.domain.com:8443` to visit the website.


