---
keyword: [alibaba cloud ssl certificate, iis server, support https]
---

# Install SSL certificates on IIS servers

Alibaba Cloud SSL Certificates Service allows you to download an SSL certificate and install it on an Internet Information Services \(IIS\) server. This way, HTTPS can be enabled on the IIS server. This topic describes how to install an SSL certificate on an IIS server.

-   An IIS server is installed and port 443 is enabled on your IIS server. This port is the default port for the HTTPS service.
-   The OpenSSL tool is installed.
-   An SSL certificate is downloaded for your IIS server. For more information about how to download SSL certificates, see[Download certificates](/intl.en-US/Install Certificates/Download certificates.md).

    **Note:** When you apply for an SSL certificate, you must select **Automatic** for CSR Generation. If you select **Manual**, no certificate file is generated. You must find **Other** in the Server Type column, download the CRT certificate file, and then run the openssl command to convert the format of the certificate file from CRT to PFX.


## Procedure

1.  Log on to the [SSL Certificates Service console](https://yundun.console.aliyun.com/?p=cas).

2.  On the SSL Certificates Service page, find the certificate that you want to download, and click **Download** in the Actions column.

3.  Find **IIS** in the Server Type column and click **Download** in the **Actions** column to download the IIS certificate package to your on-premises computer.

4.  Decompress the IIS server certificate package that you downloaded.

    Two files are extracted, including a certificate file suffixed with PFX or of the PFX file format and a key file suffixed with TXT or of the TXT file format.

    ![Certificate files](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255633691_en-US.png)

    **Note:** A new password file is generated each time you download the certificate. The password is valid only for the certificate you download that time. If you need to update the certificate file, update the matching key file accordingly.

5.  Log on to the Windows server where your IIS server is installed.

6.  In **IIS Manager**, import the extracted IIS server certificate file.

    1.  On the Windows server where the IIS server is installed, choose **Start** \> **Run** \> **MMC** to open IIS Manager.

    2.  Choose **File** \> **Add/Remove Snap-in**.

        ![Add/Remove Snap-in](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255633702_en-US.png)

    3.  In the **Available snap-ins** list, select **Certificates** and click **Add**. In the Certificates snap-in dialog box, select **Computer Account**. Click **Next**. In the Select Computer dialog box, select **Local computer: \(the computer this console is running on\)**.

    4.  In the left-side navigation pane of the console, click **Certificates** under **Console Root** to expand the certificate list.

        ![Expand the certificate tree list](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255633705_en-US.png)

    5.  Right-click **Personal** and choose **All Tasks** \> **Import**. In the **Certificate Import Wizard**, click **Next**.

        ![Open the Certificate Import Wizard](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255633706_en-US.png)

    6.  In the File to Import step, click **Browse** to import the downloaded PFX certificate file, and then click **Next**.

        ![Import certificates](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255633837_en-US.png)

        **Note:** In the Open dialog box, select **All Files \(\*.\*\)** from the file type drop-down list on the right of **File name**.

    7.  Enter the password that is in the certificate key file and click **Next**.

        You can open the pfx-password.txt file in the downloaded IIS server certificate file to retrieve the password.

        ![Enter the certificate key](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255633838_en-US.png)

    8.  Select **Automatically select the certificate store based on the type of certificate** and click **Next** to complete the import.

        ![Select certificate store](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/66003/156447255733839_en-US.png)

7.  Assign a certificate for the server.

    1.  Open IIS Manager \(IIS 8.0\), find the website where you want to install the certificate, and then click **Bind**.

    2.  In the **Site Bindings** dialog box, choose **Add** \> **https** \> **443** \> **SSL certificate** \> **OK**.

        **Note:** The default port for SSL is port 443, which cannot be changed. If you use other ports, such as 8443, enter `https://www.domain.com:8443` to visit the website.


## What to do next

After you complete certificate installation, you can verify it by accessing the domain name that is bound to the certificate.

```
https://yourdomain.com   # Replaces yourdomain.com with the domain name that is bound to your certificate.
```

If a lock icon appears in the address bar, the certificate is installed.

If your website cannot be accessed over HTTPS after the certificate is installed, check whether the port 443 on the server where you install the certificate is enabled or blocked by other tools. If you use an Alibaba Cloud Elastic Compute Service \(ECS\) instance, log on to the ECS console and allow inbound traffic to the port 443 on the **Security Groups** page.

## References

-   [Install SSL certificates on Tomcat servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md)
-   [Install SSL certificates on Apache servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates on Apache servers.md)
-   [Deploy SSL certificates on Apache 2 servers that run Ubuntu](/intl.en-US/Install Certificates/Install certificates to servers/Deploy SSL certificates on Apache 2 servers that run Ubuntu.md)
-   [How do I deploy the issued certificate in Apache server]()
-   [Install an SSL certificate on an NGINX server or a Tengine server](/intl.en-US/Install Certificates/Install certificates to servers/Install an SSL certificate on an NGINX server or a Tengine server.md)
-   [Deploy SSL certificates on Tomcat 8.5 or 9.0 servers that run CentOS](/intl.en-US/Install Certificates/Install certificates to servers/Deploy SSL certificates on Tomcat 8.5 or 9.0 servers that run CentOS.md)
-   [Install SSL certificates on Jetty servers](/intl.en-US/Install Certificates/Install certificates to servers/Install SSL certificates on Jetty servers.md)

