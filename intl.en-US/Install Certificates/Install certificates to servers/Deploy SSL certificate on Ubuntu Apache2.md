# Deploy SSL certificate on Ubuntu Apache2

This manual describes how to install the Alibaba Cloud SSL certificate in Apache2 on Ubuntu.

## Environment

OS: Ubuntu

Web server: Apache2

## Prerequisites

-   The Apache server certificate is downloaded from the [Alibaba Cloud SSL certificate services console](https://yundunnext.console.aliyun.com/?spm=5176.2020520155.aliyun_sidebar.30.25af2a528ujbXD&p=cas#/overview/cn-hangzhou).
-   Open SSL is installed.

## Steps

1.  In apache2 directory, execute the following command to create ssl directory.

    `mkdir /etc/apache2/ssl`

2.  Execute the following command to copy the downloaded Alibaba Cloud certificate file to ssl directory.

    `cp -r YourDomainName_public.crt /etc/apache2/ssl`

    `cp -r YourDomainName_chain.crt /etc/apache2/ssl`

    `cp -r YourDomainName.key /etc/apache2/ssl`

3.  Execute the following command to enable the SSL module.

    `sudo a2enmod ssl`

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/93419/156447311336989_en-US.png)

    After the SSL module is enabled, you can execute `ls /etc/apache2/sites-available` and view the default-ssl.conf file created in the directory.

    **Note:** Port 443 is a network browsing port that is used primarily for HTTPS services. After the SSL module is enabled, port 443 is automatically released. If port 443 is not automatically released, you can execute `vi /etc/apache2/ports.conf` and add `Listen 443` to manually release it.

4.  Execute the following command to modify the configuration file default-ssl.conf for certificate installation.

    `vi /etc/apache2/sites-available/default-ssl.conf`

    In default-ssl.conf file, find the following parameters and modify the parameters. After modification is complete, click `:wq` to save and exit.

    ```
    <IfModules mod_ssl.c>
    <VirtualHost *:443>  
    ServerName #change to the domain as www.YourDomainName.com bound by the certificate.
    SSLCertificateFile /etc/apache2/ssl/www.YourDomainName_public.crt #replace/etc/apache2/ssl/www.YourDomainName.com_public.crt with certificate file path+certificate file name.
    SSLCertificateKeyFile /etc/apache2/ssl/www.YourDomainName.com.key  #replace/etc/apache2/ssl/www.YourDomainName.com.key with certificate key file path+certificate key file name.
    SSLCertificateChainFile /etc/apache2/ssl/www.YourDomainName.com_chain.crt  #replace/etc/apache2/ssl/www.YourDomainName.com_chain.crt with certificate chain file path+certificate chain file name.
                            
    ```

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/93419/156447311436991_en-US.png)

    /sites-available: This directory stores available virtual machine host; /sites-enabled: This directory stores enabled virtual machine host.

    **Note:** default-ssl.conf This file may be stored at /etc/apache2/sites-available or /etc/apache2/sites-enabled.

5.  Map default-ssl.conf to /etc/apache2/sites-enabled folder, create soft links in order to automatically link the two folders.

    ```
    sudo ln -s /etc/apache2/sites-available/default-ssl.conf /etc/apache2/sites-enabled/001-ssl.conf
    ```

6.  Reload the Apache2 configuration file.

    `sudo /etc/init.d/apache2 force-reload`

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/93419/156447311436992_en-US.png)

7.  Execute the following command to restart the Apache2 service.

    ```
    sudo /etc/init.d/apache2 restart
    ```

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/93419/156447311436993_en-US.png)


## What to do next

Apache2 service is reloaded successfully. You can enter https://www.YourDomainName.com in your explorer to validate certificate installation result.

