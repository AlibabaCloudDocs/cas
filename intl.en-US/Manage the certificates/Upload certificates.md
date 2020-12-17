---
keyword: [centralized management, deployment to cloud services]
---

# Upload certificates

You can upload third-party certificates to the SSL Certificates Service console for centralized management.

## Background

In the SSL Certificates Service console, you can upload only the **PEM**-encoded CA certificate files and private key files. If your CA certificate files or private key files are not PEM-encoded, convert them to **PEM**-encoded files before you upload the files. The CA certificate files support the PEM and CRT formats. The private key files support the KEY format. For more information about how to convert files, see [Certificate format conversion](/intl.en-US/Product Introduction/SSL certificate concepts/What formats are used for mainstream digital certificates.md).

**Note:** The certificates that you upload in the SSL Certificates Service console cannot be downloaded.

## Procedure

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  On the SSL Certificates page, click **Upload Certificate** above the certificate list.

    ![Upload a certificate ](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4626116061/p33458.png)

3.  In the Upload Certificate dialog box, specify the following parameters.

    ![Certificate files](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4626116061/p33466.png)

    |Parameter|Description|
    |---------|-----------|
    |**Certificate Name**|Enter a name for the certificate that you want to upload.The name can contain letters, digits, underscores \(\_\), and hyphens \(-\). |
    |**Certificate File**|Enter the content of the CA certificate file that is encoded in the PEM format.You can copy the content from your PEM or CRT file to this field.

**Note:** We recommend that you use a text editor, such as Notepad or Notepad++, to open your CA certificate file and private key file. |
    |**Certificate Key**|Enter the content of the private key file that is encoded in the PEM format.You can copy the content from your KEY file to this field.

**Note:** We recommend that you use a text editor, such as Notepad or Notepad++, to open your CA certificate file and private key file. |

4.  Click **OK**.

    After the certificate is uploaded, you can click the number in the **Upload Certificate** section on the **SSL Certificates** page to view the uploaded certificate.

    ![Upload a certificate](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5382726061/p183875.png)


You can deploy the uploaded certificate to Alibaba Cloud services. For more information, see [Deploy certificates on Alibaba Cloud services](/intl.en-US/Deploy the certificate to Cloud products/Deploy certificates on Alibaba Cloud services.md).

