# Domain name certificate application note

When the domain name console automatically issues a domain name association certificate, it can be automatically issued without requiring the user to apply for the certificate, there are the following prerequisites for the configuration of the relevant subsequent certificate issuance and verification file:

-   Domain name in ALI cloud WAN network
-   Cloud analytics in ALI cloud

    If cloud resolution is not in ALI cloud, the autoissue cannot be completed after the certificate application. If the user does not have the ability to configure DNS resolution, it is recommended that DNS resolution be transferred to Ali cloud, authorization is automatically configured for DNS authentication parsing records in the background so that the issue can be completed. Otherwise, you need to go to the [Alibaba Cloud shield Certificate Services console](https://account.alibabacloud.com/login/login.htm) to purchase the DV toll certificate. After that, the configuration is configured according to the DNS authentication resolution requirements in the console's progress, go to the third-party DNS resolution console to configure the specified TXT authentication resolution, it is used to prove the user's administration of the domain name before the certificate is issued.

    If cloud resolution is not in ALI cloud, the autoissue cannot be completed after the certificate application. If the user does not have the ability to configure DNS resolution, it is recommended that DNS resolution be transferred to Ali cloud, authorization is automatically configured for DNS authentication parsing records in the background so that the issue can be completed.

    When there is a large number of certificate-issuing requirements, it is recommended that you transfer DNS resolution to Ali cloud, certificate Application and management work can be greatly simplified.

-   Domain Name certified by real name
-   Domain name within the effective period

Free certificates

-   Domain Name and resolution are required in ALI cloud to issue a free certificate

    The free certificate is very large for personal users and testing purposes in the Ali cloud platform, in order to improve the user automation interaction experience, it is necessary for users to move domain names and cloud resolution into the Alibaba Cloud, to complete the issuance of free certificates.

-   Issue quantity limit

    The maximum number of issues for a free certificate per day is 20. Only until the next day \(24 hours later\) when the quota user of the one-day free certificate is finished\) the issue of the new free certificate will not continue until the new certificate is issued. Based on this calculation, an Alibaba Cloud real-name authentication account, the maximum number of free certificates issued a year is 7300 free SSL digital certificates.

-   Free Certificate No SLA guarantee, it is recommended that commercial websites issue toll certificates

For certificate-related questions, please contact us with cloud shield certificate service orders. Thank you for your support to Ali cloud!

