# OSS用户申请SSL证书注意事项

本文档介绍了阿里云OSS用户申请SSL证书的注意事项。

您可以登录[OSS管理控制台](https://oss.console.aliyun.com/)对证书进行以下操作：

-   申请签发新的SSL证书。
-   上传已有证书进行托管。

OSS用户申请SSL证书的具体操作，请参见[证书托管](/intl.zh-CN/控制台用户指南/存储空间管理/管理域名/证书托管.md)。

## 付费版Entrust OV SSL证书、GlobalSign OV和EV SSL证书

您的域名需要在阿里云才可在证书申请完成后自动签发。

如果您的域名解析不在阿里云，证书申请后将无法完成自动签发，需要您登录阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)按照证书**状态**提示自行配置。

**说明：**

如果您无法配置DNS解析，建议您把DNS解析转入阿里云，授权后台自动进行DNS验证解析记录配置，这样才可完成签发。否则，需要您登录阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)购买收费证书后，根据控制台进度中DNS验证解析配置要求，去第三方的DNS解析控制台配置指定的TXT验证解析，用于证明您对该域名的管理权，方可签发证书。

如果您有大量的证书签发需求，建议您把DNS解析转入阿里云，可以大量简化您的证书申请及管理工作量。

