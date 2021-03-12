# FAQ about deploying certificates to cloud products

Digital certificates purchased from Alibaba Cloud Certificates Service can be deployed to Alibaba Cloud products like CDN, SCDN, DCDN and Server Load Balancer with a single click.

Do not deploy your certificate to any products or services that you have not purchased. Because these products or services cannot recognize the domain name associated with your certificate. The deploying process may fail.

**Note:** But, Server Load Balance is an exception to this restriction. The deploying process can be successful even if the service is not enabled.

## When a certificate has been successfully deployed to a cloud product, does that mean the HTTPS service works properly for the cloud product?

No. You still need to configure some parameters in the cloud product console. Additionally, make sure that your origin server is appropriately prepared for HTTPS support.

For the required parameter settings for each cloud product, see [Certificate overview](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Create a certificate/Certificate overview.md) and [t5134.md\#](/intl.en-US/Domain Management/HTTPS/Configure an SSL certificate.md).

## Why I do not find my domains when deploying the certificates to CDN?

When deploying a digital certificate to CDN, the certificate service first checks if the domains available in CDN match those in the certificate. One reason for the failure is that you have not configured or enabled the domains associated with the certificate in the CDN console.

Go to the CDN console to add the domains associated with your certificate, and then enable them. See [t5134.md\#](/intl.en-US/Domain Management/HTTPS/Configure an SSL certificate.md).

**Note:** The certificate service can only find appropriately working domains when querying the domain list in the CDN console.

## When a digital certificate is deployed to Server Load Balance, to which regions is it deployed?

The certificate service deploys a copy of the certificate to all regions. Canceling the deployment removes the deployed copies from the respective regions.

After the certificate is deployed to Server Load Balance in various regions, select your Server Load Balance instance from the **Server Load Balancer console** \> **Instance Management** and then click **Manage**. On the Listener page, click **Add Listener**, and then configure the listener details with the certificate selected.

**Note:** Make sure that the selected certificate and the added domains are matched.

## After certificate information has been modified in SSL console, do I need to deploy the certificate information again to the cloud product?

Yes. When a SSL certificate has been modified, please [t65315.md\#](/intl.en-US/Install Certificates/Deploy certificates on Alibaba Cloud services.md), so the modified certificate information can be synchronized. If not, information in the cloud product and the modified certificate are unmatched.

