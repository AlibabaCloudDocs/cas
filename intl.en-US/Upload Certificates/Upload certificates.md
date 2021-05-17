# Upload certificates

If you have Secure Sockets Layer \(SSL\) certificates that are purchased from and issued by a third-party certificate service provider, you can upload your certificates to the SSL Certificates Service console. Then, you can deploy your certificates to Alibaba Cloud services and manage all your certificates in a centralized manner. This topic describes how to upload a certificate to the SSL Certificates Service console.

The following files are prepared for the certificate that you want to upload:

-   A PEM-encoded certificate authority \(CA\) certificate file in the PEM or CRT format
-   A PEM-encoded private key file in the KEY format

**Note:** In the SSL Certificates Service console, you can upload only the **PEM**-encoded CA certificate files and private key files. If your CA certificate files or private key files are not PEM-encoded, you must convert them to **PEM**-encoded files before you upload the files. For more information about how to convert files, see [Certificate format conversion](/intl.en-US/Product Introduction/SSL certificate concepts/What formats are used for mainstream digital certificates?.md).

## Usage notes

After you upload a certificate to the SSL Certificates Service console, you cannot download the certificate. This helps ensure the data security of your certificate.

## Procedure

1.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).

2.  On the **Overview** page, click **Upload Certificate** above the certificate list.

3.  In the **Upload Certificate** dialog box, configure the following parameters.

    ![Certificate files](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4626116061/p33466.png)

    |Parameter|Description|
    |---------|-----------|
    |**Certificate Name**|Enter a name for the certificate that you want to upload. The name can contain letters, digits, underscores \(\_\), and hyphens \(-\). |
    |**Certificate File**|Enter the content of the PEM-encoded CA certificate file. You can use two methods to enter the content. Method 1: Use a text editor, such as Notepad or Notepad++, to open the CA certificate file in the PEM or CRT format. Then, copy the content to the Certificate File field. Method 2: Click **Upload** below the Certificate File field. Then, select the CA certificate file from your computer to upload the content of the file. |
    |**Certificate Key**|Enter the content of the PEM-encoded private key file. You can use two methods to enter the content. Method 1: Use a text editor, such as Notepad or Notepad++, to open the private key certificate file in the KEY format. Then, copy the content to the Certificate Key field. Method 2: Click **Upload** below the Certificate Key field. Then, select the private key file from your computer to upload the content of the file. |

4.  Click **OK**.

    After the certificate is uploaded, you can view the certificate in the certificate list.


## What to do next

You can deploy the uploaded certificate to Alibaba Cloud services. For more information, see [Deploy a certificate to an Alibaba Cloud service](/intl.en-US/Install Certificates/Deploy a certificate to an Alibaba Cloud service.md).

