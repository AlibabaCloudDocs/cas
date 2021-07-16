# How do I configure domain name authorization?

According to the CA center specification, if you are applying for a free or DV-type digital certificate, you must work together with the completion of the domain name authorization verification to prove your ownership of the domain name to which the application is bound. If you submit an audit of a different type of digital certificate, you do not need to configure domain name authorization information. As long as the domain name authorization information is configured correctly as required, the domain name authorization verification should be completed, after the CA system detection takes effect, the certificate can then be issued.

How to configure authorization authentication depends on the Authorization authentication method that you select when submitting a digital certificate audit application, for how to select a domain name authorization authentication method, see [Which domain name verification method should I choose?](/intl.en-US/Issue Certificates/FAQ/Which domain name verification method should I choose?.md).

The Alibaba Cloud shield Certificate Service provides two ways to validate:

## DNS authentication method

DNS authentication is generally required by your domain name manager. Please follow the progress prompts in your certificate order, configure in your domain name management system.

Select the DNS domain name authorization authentication method, you need to go to your domain name Resolution Service Provider \(such as web, new network, dnspod, and so on\) the provided system is configured. For example, the domain name is hosted in the Ali cloud, and you need to go to the cloud resolution DNS console for the relevant configuration.

**Note:** This DNS configuration record can be deleted after the certificate has been issued or abolished.

**Procedures**

1.  Log in to the cloud shield Certificate Services Management Console, select the certificate order in my list of orders for which you have submitted an audit request, and click progress, you can view information about the domain name authorization configuration, such as the host records for DNS that need to be configured, record values, record types, and so on \).

    **Note:** After you submit an audit request, the system may take several minutes to generate the relevant domain name authorization configuration information.

2.  Add a record to your domain name resolution management system based on the domain name authorization Configuration Requirements. Be sure to correctly fill in the host records, record values, and record types, note do not reverse the host records and record values configuration.

    **Note:** The cloud shield Certificate Service provides a host record with a full domain name, if your domain name management system does not support full domain name host records, remove the suffix section of the root domain name..

    **Note:** If your domain name is hosted in Alibaba Cloud's cloud Resolution Service and the authorization system is checked to automatically add a record to complete the domain name authorization validation option, you do not need to do anything in the domain name resolution administration console. You can view the domain name authorization push results directly on the Audit Progress page:

    -   If the push is successful, you only have to wait for the certificate to be issued.
    -   If the push fails, you need to re-configure it manually, see the Domain Name authentication push to Ali cloud DNS failed for details. What should I do?
3.  The detection configuration takes effect. Please refer to the DNS detection section in [What do I do if my certificate order remains in the review stage for a long time?](/intl.en-US/Issue Certificates/FAQ/What do I do if my certificate order remains in the review stage for a long time.md)

## File validation method

File validation methods typically require operations by your site administrator. Please follow the prompts on the Progress page in your certificate order to download the file to your local computer, then upload through tools, such as FTP, to the specified directory on your server.

**Note:** This authentication file can be deleted after the certificate has been issued or abolished.

**Procedures**

1.  Log in to the cloud shield Certificate Services Management Console, select the certificate order in my list of orders for which you have submitted an audit request, and click progress, you can view information about the domain name authorization configuration, such as the Authentication Files that need to be uploaded and the specified server directory, etc. \).
2.  Downloads the specified authentication file to the local computer, as required by the configuration, then upload through tools, such as FTP, to the specified directory on your server.

    For example, the domain name of your website is a.com, the disk directory for the server on which the site is located is/www/htdocs. According to the above File validation Configuration Requirements, You need to configure as follows:

    1.  Verify the file and download it locally.
    2.  Create in the directory/www/htdocs of your site server. well-maid/Katherine-validation sub-directory.
    3.  The authentication file is uploaded to the/www/htdocs/. Well-FIG/Katherine-validation directory.
    4.  After completion, you can verify the URL address \(http://a.com/.well-known/pki-validation/fileauth.txt \) Access.
3.  The detection configuration takes effect. You can verify that the URL address is properly accessed through the browser to detect that the configuration is in effect. For more information on the effectiveness of the inspection configuration, please refer to the file detection in [What do I do if my certificate order remains in the review stage for a long time?](/intl.en-US/Issue Certificates/FAQ/What do I do if my certificate order remains in the review stage for a long time.md).

