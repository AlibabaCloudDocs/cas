# 【重要】GlobalSign更新DV SSL中间根证书说明

GlobalSign于2021年1月21日，更新了DV SSL中间根证书，具体公告如下：

亲爱的阿里云用户，您好：

为了符合Certificate Authority Browser Forum（证书管理局）对于SSL证书的安全规范和要求，GlobalSign已对DV SSL的中间根证书进行了升级。旧的中间证书（型号：**GlobalSign RSA DV SSL CA 2018**）已经被更换为新的中间证书（型号：**GlobalSign GCC R3 DV TLS CA 2020**）。本次升级提高了DV SSL证书的安全性能。

由于开发新的中间证书的过程包含多方的审核、测试，导致我们在通知上出现了延迟。我们对此表示歉意。

我们将配合阿里云，帮助每一位用户重新签发证书。您只需要按照原来的安装方式，把重新签发的证书安装到您的服务器，无需更换公钥和私钥。

非常感谢大家一直以来对GlobalSign的支持。对于此通告，我们再次表示歉意。

谢谢

GlobalSign APAC

## 阿里云解决方案

由于GlobalSign DV SSL中间根证书的更新，导致2021年1月21日0时0分0秒前通过阿里云SSL证书服务签发的GlobalSign DV SSL证书已被吊销。GlobalSign将于2021年1月22日前，对所有涉及重新签发的DV SSL证书进行批量签发，阿里云会使用新签发的证书覆盖原有证书。

如果您使用了GlobalSign的DV SSL证书，需要前往[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)重新下载新签发的证书，并将新签发的证书重新安装到服务器，替换原有的证书，才能恢复网站的HTTPS访问。

在安装过程中遇到问题时，请联系我们获取一对一加急技术指导。

## 阿里云补偿方案

所有涉及到重新安装GlobalSign DV SSL证书的用户，在下次使用GlobalSign证书时，将享受1次原价基础上的5折优惠。

