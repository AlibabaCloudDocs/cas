# \[Change\] Notice on policy changes for domain ownership verification

Valued Alibaba Cloud users,

SSL Certificates Service will adjust the **file-based verification** method for domain ownership verification based on the latest proposal of .

**Effective date**: September 21, 2021.

**Changes**:

-   Wildcard domain name: You can no longer use the file-based verification method to verify the ownership of a wildcard domain name such as \*.example.com or \*.1.example.com.

    If you apply for a certificate that protects a wildcard domain name by using SSL Certificates Service, you can verify the ownership of the wildcard domain name only by adding a DNS record. For more information about how to add a DNS record to prove the ownership of a domain name, see [DNS authentication method](/intl.en-US/Issue Certificates/FAQ/How do I configure domain name authorization?.md).

-   Single domain name: You can still use the file-based verification method to verify the ownership of a single domain name. A single domain name can be a primary domain name such as example.com or be a subdomain name such as www.example.com. The file-based verification method requires that each single domain name be separately verified.

    If you use the file-based verification method to verify the ownership of a primary domain name such as example.com, you must also verify the ownership of each of its subdomain names such as www.example.com. For more information about file-based verification, see [File validation method](/intl.en-US/Issue Certificates/FAQ/How do I configure domain name authorization?.md).


**References**: [Domain validation policy changes in 2021](https://knowledge.digicert.com/alerts/domain-authentication-changes-in-2021.html)

We apologize for the inconvenience that may be caused. If you have questions, submit a [ticket](https://ticket-intl.console.aliyun.com/#/ticket/add/?productId=80) to contact us.

