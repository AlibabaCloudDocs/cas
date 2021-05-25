# Apache Tomcat及httpd服务器安装SSL证书教程

观看以下视频，快速了解如何在Apache Tomcat 7、Apache Tomcat 8、Apache httpd 2服务器上安装SSL证书。



## 准备工作及测试环境介绍

本视频包含Apache Tomcat 7安装SSL证书、Apache Tomcat 8安装SSL证书、Apache httpd 2安装SSL证书三个部分。不同部分所需的准备工作相同，且仅在视频前面有说明。

为方便您直接观看感兴趣的部分，以下内容介绍了在服务器安装证书前，您需要完成的准备工作：

-   已通过[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)下载对应服务器类型的SSL证书。

    关于下载证书的具体操作，请参见[t123605.md\#section\_cjh\_359\_s85](/cn.zh-CN/证书安装/SSL证书安装指南.md)。

-   已将下载的证书上传到服务器。推荐您在服务器的Web程序目录下创建`/cert`目录，并将已下载的证书上传到该目录。

    本视频中，适用于Apache Tomcat服务器的证书已上传到`/opt/apache-tomcat-XX.XX.XX/cert`目录并解压缩，适用于Apache httpd服务器的证书已上传到`/etc/httpd/conf/cert`目录并解压缩。

    如果您不清楚如何上传证书到服务器，推荐您使用[WinSCP](https://winscp.net/eng/download.php)工具。


本教程使用的测试资源及Web服务环境如下表所示。

|教程|测试域名|Web服务程序版本|视频起止片段|
|--|----|---------|------|
|Apache Tomcat 7安装SSL证书|doc.测试.club|apache-tomcat-7.0.108|01分30秒~03分20秒|
|Apache Tomcat 8安装SSL证书|doc.测试.club|apache-tomcat-8.5.64|03分21秒~05分10秒|
|Apache httpd 2安装SSL证书|test.测试.club|httpd-2.4.6|05分11秒~08分40秒|

