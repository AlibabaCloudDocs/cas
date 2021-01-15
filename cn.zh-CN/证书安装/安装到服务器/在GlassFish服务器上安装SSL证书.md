---
keyword: [阿里云SSL证书, GlassFish服务器, 支持HTTPS]
---

# 在GlassFish服务器上安装SSL证书

阿里云SSL证书服务支持下载证书安装到Glassfish服务器上，本文介绍了证书安装的具体操作。

本文中证书名称以**cer01**为示例，如证书文件名称为**cer01.pem**，证书密钥文件名称为**cer01.key**。

## 操作步骤

1.  在SSL证书页面，定位到需要下载的证书实例并单击证书卡片右下角的**下载**。

    ![下载](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2256669951/p39167.jpg)

2.  定位到**其他**服务器类型，并单击右侧**操作**栏的**下载**将证书压缩包下载到本地。

3.  解压已下载保存到本地的证书文件。您将看到文件中有一个证书文件（以.pem为后缀或文件类型）和一个密钥文件（以.txt为后缀或文件类型）。

    ![证书文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9144495751/p34118.png)

4.  输入以下两行命令将证书和密钥文件转换成JKS格式。

    ```
    openssl pkcs12 -export -in cer01.pem -inkey cer01.key -out temp.p12 -passout pass:changeit -name s1as
    #请用您的证书名称替换命令行中cer01.pem、用您的证书密钥替换cer01.key。转换证书格式时设置的密码必须和您Glassfish服务器中自带的证书密码一致，该证书默认密码是changeit。
    ```

    ```
    keytool -importkeystore -srckeystore temp.p12 -srcstoretype PKCS12 -srcstorepass changeit -deststoretype JKS -destkeystore ./glassfish5/glassfish/domains/domain1/config/keystore.jks -deststorepass changeit -alias s1as
    #转换证书格式时设置的密码必须和您Glassfish服务器中自带的证书密码一致，该证书默认密码是changeit。
    ```

5.  重启domain。

    ```
    ./glassfish5/bin/asadmin restart-domain
    ```

6.  检查您阿里云证书绑定的域名是否生效。

    ```
    wget https://10.0.0.1:8181
    ```


