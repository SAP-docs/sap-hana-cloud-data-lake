<!-- loiofe6ef484b3da4dfc87c278a227b9ffad -->

# CREATE X509 PROVIDER Statement for Data Lake Relational Engine

Create an X.509 provider in the database.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



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
<x509_provider_name> ::= <simple_identifier>
```



</dd><dt><b>

*<issuer\_clause\>*

</b></dt>
<dd>

Sets the issuer distinguished name for the provider.

```
<issuer_clause> ::= WITH ISSUER <issuer_distinguished_name>

<issuer_distinguished_name> ::= <string_literal>
```



</dd><dt><b>

*<matching\_rules\_clause\>*

</b></dt>
<dd>

Specifies one or more rules for matching external identities to database users. A matching rule is a distinguished name where one attribute includes a wildcard \(\*\), which can be pre- and/or post-fixed. For example, user\_\*, \*\_user, or sap\*\_user. This attribute contains the user name that needs to be matched during logon. All other attributes must match and be in the same order.

```
<matching_rules_clause> ::= MATCHING RULES '<subject_distinguished_name_mapping>'
[, '<subject_distinguished_name_mapping>' ... ]

<subject_distinguished_name_mapping> ::= <string_literal>
```

Matching rules are tried in the same order they are defined in the provider, and the first one that matches is used. For additional information on matching rules, see [X.509 Certificate-Based User Authentication](https://help.sap.com/viewer/745778e524f74bb4af87460cca5e62c4/2023_2_QRC/en-US/c9bf672bbc2849568a1ff1d2fbc9a78d.html "Data lake Relational Engine supports X.509 client certificates for user authentication.") :arrow_upper_right:.



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
   WITH ISSUER 'CN=DigiCert Global Root CA, OU=www.digicert.com, O=DigiCert Inc, C=US';
```

This example creates an X.509 provider named MyProvider2 that contains a matching rule.

```
CREATE X509 PROVIDER MyProvider2
   WITH ISSUER 'CN=DigiCert Global Root CA, OU=www.digicert.com, O=DigiCert Inc, C=US'  
   MATCHING RULES 'CN=*, OU=SAP SE, C=DE';
```

