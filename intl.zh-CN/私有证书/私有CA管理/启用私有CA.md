# 启用私有CA

创建私有CA后，您必须启用私有CA，才能使私有CA正式生效（可以用于签发私有证书）。本文介绍了启用私有CA的操作方法。

已创建私有CA。相关操作，请参见[创建私有CA](/intl.zh-CN/私有证书/私有CA管理/创建私有CA.md)。

**说明：** 私有CA启用后，将不支持退款。更多信息，请参见[申请退款](/intl.zh-CN/私有证书/私有CA管理/申请退款.md)。

## 步骤1：启用私有根CA

首次启用私有CA时，您必须先启用根CA，再启用子CA。如果根CA已经启用，则可以跳过该步骤，直接启用根CA下的子CA。

1.  登录[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)。

2.  在左侧导航栏，单击**私有证书**。

3.  在**私有证书**页面，定位到要启用的根CA（**未启用**状态），单击**操作**列下的**启用**。

4.  在**CA信息**面板，配置根CA的信息。

    ![启用CA](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3896416161/p253399.png)

    配置说明如下表所示。

    |参数|说明|
    |--|--|
    |**组织机构（O）**|该CA关联的组织机构的名称。支持使用中文或者英文。示例：阿里云计算有限公司。 |
    |**组织部门（OU）**|该CA关联的组织部门的名称。支持使用中文或者英文。示例：IT部。 |
    |**公用名（CN）**|该CA关联的组织机构的通用名称（或简称）。支持使用中文或者英文。示例：阿里云。 |
    |**国家/地区（C）**|组织机构所在国家名称。支持使用中文或者英文。示例：中国。 |
    |**省名称（S）**|组织机构所在省份名称。支持使用中文或者英文。示例：浙江。 |
    |**城市名称（L）**|组织机构所在城市名称。支持使用中文或者英文。示例：杭州。 |
    |**私钥算法**|该CA使用的私钥加密算法。根据您在购买该PCA服务时选择的**加密算法**不同，此处支持选择私钥算法也不同。具体说明如下：

    -   如果CA加密算法是**RSA**，则此处私钥算法的可选项包括：**RSA\_1024**、**RSA\_2048**、**RSA\_4096**。
    -   如果CA加密算法是**SM（国密）**，则此处私钥算法的可选项包括：**SM2\_256**、**SM2\_384**、**SM2\_512**。
    -   如果CA加密算法是**ECC**，则此处私钥算法的可选项包括：**ECC\_256**、**ECC\_384**、**ECC\_512**。 |
    |**有效期**|该CA的有效时长。可选项：**5年**、**10年**、**15年**、**20年**。|

5.  单击**确认并启用**。

6.  在**提示**对话框，单击**确定**。

    ![提示](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3443098161/p266061.png)

    成功启用根CA后，根CA的状态将变更为**启用**。


## 步骤2：启用私有子CA

只有启用根CA后，您才可以启用根CA下的子CA。

1.  登录[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)。

2.  在左侧导航栏，单击**私有证书**。

3.  在**私有证书**页面，定位到要启用的子CA（**未启用**状态），单击**操作**列下的**启用**。

    **说明：** 如果子CA隶属的根CA还未启用，则不支持直接启用子CA。

4.  在**CA信息**面板，配置子CA的信息。

    ![启用CA](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3896416161/p253399.png)

    配置说明如下表所示。

    |参数|说明|
    |--|--|
    |**组织机构（O）**|该CA关联的组织机构的名称。支持使用中文或者英文。示例：阿里云计算有限公司。 |
    |**组织部门（OU）**|该CA关联的组织部门的名称。支持使用中文或者英文。示例：IT部。 |
    |**公用名（CN）**|该CA关联的组织机构的通用名称（或简称）。支持使用中文或者英文。示例：阿里云。 |
    |**国家/地区（C）**|组织机构所在国家名称。支持使用中文或者英文。示例：中国。 |
    |**省名称（S）**|组织机构所在省份名称。支持使用中文或者英文。示例：浙江。 |
    |**城市名称（L）**|组织机构所在城市名称。支持使用中文或者英文。示例：杭州。 |
    |**私钥算法**|该CA使用的私钥加密算法。根据您在购买该PCA服务时选择的**加密算法**不同，此处支持选择私钥算法也不同。具体说明如下：

    -   如果CA加密算法是**RSA**，则此处私钥算法的可选项包括：**RSA\_1024**、**RSA\_2048**、**RSA\_4096**。
    -   如果CA加密算法是**SM（国密）**，则此处私钥算法的可选项包括：**SM2\_256**、**SM2\_384**、**SM2\_512**。
    -   如果CA加密算法是**ECC**，则此处私钥算法的可选项包括：**ECC\_256**、**ECC\_384**、**ECC\_512**。 |
    |**有效期**|该CA的有效时长。可选项：**5年**、**10年**、**15年**、**20年**。|

5.  单击**确认并启用**。

6.  在**提示**对话框，单击**确定**。

    ![提示](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3443098161/p266061.png)

    成功启用子CA后，子CA的状态将变更为**启用**。


## 后续步骤

[申请私有证书](/intl.zh-CN/私有证书/私有证书管理/申请私有证书.md)：您依次启用根CA和子CA后，可以通过已启用的子CA申请私有证书。

## 相关操作

[吊销私有CA](/intl.zh-CN/私有证书/私有CA管理/吊销私有CA.md)：在私有CA到期前，如果您不想继续使用私有CA，可以吊销私有CA。

