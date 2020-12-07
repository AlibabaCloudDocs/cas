# 开通一键式HTTPS服务

一键式HTTPS是阿里云SSL证书产品提供的增值服务，帮助您为域名下所有页面一键配置HTTPS访问。

一键式HTTPS服务需要单独购买和开通。有关计费的详细介绍，请参见[增值服务](/cn.zh-CN/计量计费/计费方式.md)。

有关一键式HTTPS功能的详细介绍，请参见[功能优势](/cn.zh-CN/SSL证书增值服务/一键式HTTPS.md)。

## 限制说明

-   为您的域名开启了一键式HTTPS后，只是这个域名下的所有页面都支持HTTPS访问，HTTPS访问不对该域名以外其他级别的域名（包括通配符域名）生效。

    例如：已为aliyun.com开启了一键式HTTPS服务，该服务仅对aliyun.com生效。生效范围不包括除aliyun.com以外的其他级别域名（如forum.aliyun.com、image.forum.aliyun.com、\*.aliyun.com）。

-   只有完成网站备案的域名才能使用一键式HTTPS服务。

    建议您在购买一键式HTTPS服务前先完成网站备案。有关备案的详细内容请参见[什么是备案]()。

-   源站地址不可输入有安全防护及加速功能产品的IP地址或域名（如Web应用防火墙、CDN、DDoS高防等）。如果输入了此类地址或域名，为避免您使用的这些安全防护和加速产品失效或减弱防护能力，HTTPS服务会提示您“不支持该类型的地址回源”。

## 操作步骤

1.  登录阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)。

2.  在左侧导航栏单击**一键式HTTPS** \> **资源包管理** \> **购买资源包**。

3.  在**一键式HTTPS**购买页面，选择您需要的套餐配置和套餐时长。

4.  单击**立即购买**并完成支付。


## 相关问题

[如何根据QPS阈值选择一键式HTTPS资源包套餐？](/cn.zh-CN/一键式HTTPS/常见问题/如何根据QPS阈值选择一键式HTTPS资源包套餐？.md)

[网站QPS超过套餐内最大QPS后怎么办？](/cn.zh-CN/一键式HTTPS/常见问题/网站QPS超过套餐内最大QPS后怎么办？.md)

[已启用HTTPS服务的网站可以更换HTTPS套餐吗？](/cn.zh-CN/一键式HTTPS/常见问题/已启用HTTPS服务的网站可以更换HTTPS套餐吗？.md)

