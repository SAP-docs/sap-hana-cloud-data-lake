<!-- loiofe6ef484b3da4dfc87c278a227b9ffad -->

# CREATE X509 PROVIDER Statement for Data Lake Relational Engine

Create an X.509 provider in the database.



<a name="loiofe6ef484b3da4dfc87c278a227b9ffad__section_xv3_wvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE X509 PROVIDER <x509_provider_name> <issuer_clause> [ <matching_rules_clause> ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



## Parameters


<dl>
<dt><b>

*<x509\_provider\_name\>*

</b></dt>
<dd>

Specifies the unique name of an X.509 provider.

```
<x509_provider_name> ::= <simple_identifier>;
```



</dd><dt><b>

*<issuer\_clause\>*

</b></dt>
<dd>

Sets the issuer distinguished name for the provider.

```
<issuer_clause> ::= WITH ISSUER <issuer_distinguished_name>

<issuer_distinguished_name> ::= <string_literal>;
```



</dd><dt><b>

*<matching\_rules\_clause\>*

</b></dt>
<dd>

Specifies one or more rules for matching external identities to database users. A matching rule is a distinguished name where one attribute includes a wildcard \(\*\), which can be pre- and/or post-fixed. For example, user\_\*, \*\_user, or sap\*\_user. This attribute contains the user name that needs to be matched during logon. All other attributes must match and be in the same order.

```
<matching_rules_clause> ::= MATCHING RULES '<subject_distinguished_name_mapping>'
[, '<subject_distinguished_name_mapping>' ... ]

<subject_distinguished_name_mapping> ::= <string_literal>;
```

Matching rules are tried in the same order they are defined in the provider, and the first one that matches is used. For additional information on matching rules, see [X.509 Certificate-Based User Authentication](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_1_QRC/en-US/c9bf672bbc2849568a1ff1d2fbc9a78d.html "Data lake Relational Engine supports X.509 client certificates for user authentication.") :arrow_upper_right:.



</dd>
</dl>



<a name="loiofe6ef484b3da4dfc87c278a227b9ffad__section_h3s_1bd_rwb"/>

## Privileges

Requires the MANAGE ANY USER system privilege.



<a name="loiofe6ef484b3da4dfc87c278a227b9ffad__section_yq3_bbd_rwb"/>

## Examples

This example creates an X.509 provider named MyProvider1.

```
CREATE X509 PROVIDER MyProvider1
   WITH ISSUER 'CN=DigiCert Global Root G2, OU=www.digicert.com, O=DigiCert Inc, C=US';
```

This example creates an X.509 provider named MyProvider2 that contains a matching rule.

```
CREATE X509 PROVIDER MyProvider2
   WITH ISSUER 'CN=DigiCert Global Root G2, OU=www.digicert.com, O=DigiCert Inc, C=US'  
   MATCHING RULES 'CN=*, OU=SAP SE, C=DE';
```

> ### Note:  
> You can find details about root certificate updates on the DigiCert website at [https://knowledge.digicert.com/general-information/digicert-root-and-intermediate-ca-certificate-updates-2023](https://knowledge.digicert.com/general-information/digicert-root-and-intermediate-ca-certificate-updates-2023). Also see SAP Note [3397584](https://me.sap.com/notes/3397584), SAP Note [3327214](https://me.sap.com/notes/3327214) and SAP Note [3399572](https://me.sap.com/notes/3399572).

**Related Information**  


[ALTER X509 PROVIDER Statement for Data Lake Relational Engine](alter-x509-provider-statement-for-data-lake-relational-engine-831d802.md "Alter an X.509 provider in the database.")

[DROP PROVIDER Statement for Data Lake Relational Engine](drop-provider-statement-for-data-lake-relational-engine-c20d71c.md "Drops a JWT or x509 provider from the data lake Relational Engine database.")

[X.509 Certificate-Based User Authentication](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_1_QRC/en-US/c9bf672bbc2849568a1ff1d2fbc9a78d.html "Data lake Relational Engine supports X.509 client certificates for user authentication.") :arrow_upper_right:

[SYSX509LOGINMAP System View for Data Lake Relational Engine](../070-system-and-monitoring-views/sysx509loginmap-system-view-for-data-lake-relational-engine-216c79a.md "The SYSX509LOGINMAP system view lists the X509 certificate-to-user mappings configured in the data lake Relational Engine database.")

[SYSX509PROVIDERRULES System View for Data Lake Relational Engine](../070-system-and-monitoring-views/sysx509providerrules-system-view-for-data-lake-relational-engine-f884c9b.md "The SYSX509PROVIDERRULES system view contains all of the matching rules for X.509 providers.")

[SYSX509PROVIDERS System View for Data Lake Relational Engine](../070-system-and-monitoring-views/sysx509providers-system-view-for-data-lake-relational-engine-4b29eff.md "The SYSX509PROVIDERS system view contains a list all of the X.509 providers configured in the database.")

[SYSCERTIFICATE System View for Data Lake Relational Engine](../070-system-and-monitoring-views/syscertificate-system-view-for-data-lake-relational-engine-a34ee8b.md "Each row of the SYSCERTIFICATE system view stores a certificate in text PEM-format. This view includes certificates with and without an associated PSE.")

[CREATE CERTIFICATE Statement for Data Lake Relational Engine](create-certificate-statement-for-data-lake-relational-engine-816b6bb.md "Adds or replaces a certificate in the database using the given file or string.")

