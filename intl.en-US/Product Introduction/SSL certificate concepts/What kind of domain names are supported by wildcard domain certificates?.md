# What kind of domain names are supported by wildcard domain certificates?

Alibaba Cloud SSL Certificates Service supports wildcard domain certificates. You can install a wildcard domain certificate on a server to protect a parent domain name and all its subdomains of the same level. Both the Domain Validation \(DV\) and Organization Validation \(OV\) certificates of the professional version support wildcard domain names.

If your server hosts multiple subdomain names of the same level, you do not need to purchase and install a certificate for each subdomain.

If you want to purchase a **wildcard domain** certificate, take note of the following rules to match the subdomains of the **wildcard domain name**:

-   A wildcard domain certificate supports only the subdomains of the same level.

    For example, if a wildcard domain certificate is bound with the domain name \*.example.com, it supports subdomains of the same level, such as abc.example.com, sport.example.com, and good.example.com. However, it does not support subdomains that reside at different levels, such as mycard.good.example.com and mycalc.good.example.com.

    If a wildcard domain certificate is bound with the domain name \*.good.example.com, it supports subdomains such as mycard.good.example.com and mycalc.good.example.com.

-   A wildcard domain certificate can be bound with a second-level domain name.
-   A wildcard domain certificate can be bound with only one wildcard domain name.
-   A wildcard domain certificate supports only wildcard domain names but not common domain names.

    For more information about how to use one certificate to protect multiple wildcard domain names and one or more common domain names, see [How can I apply for multi-domain wildcard certificates or hybrid certificates?](/intl.en-US/Apply for the certificate/FAQ/How can I apply for multi-domain wildcard certificates or hybrid certificates?.md).


