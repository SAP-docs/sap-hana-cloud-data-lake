<!-- loio831d802e8dd440e8a24e0ed0fd393187 -->

# ALTER X509 PROVIDER Statement for Data Lake Relational Engine

Alter an X.509 provider in the database.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER X509 PROVIDER <x509_provider_name>
   { SET { [ <issuer_clause> ] [ <matching_rules_clause> ] }
   | UNSET MATCHING RULES }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio831d802e8dd440e8a24e0ed0fd393187__section_ppx_jbd_rwb"/>

## Parameters


<dl>
<dt><b>

*<x509\_provider\_name\>*

</b></dt>
<dd>

Specifies the X.509 provider being modified.

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



</dd><dt><b>

UNSET MATCHING RULES

</b></dt>
<dd>

Removes the matching rules for the provider. If a user is mapped to the provider using a wildcard \(ANY\) subject, you cannot unset the matching rules.



</dd>
</dl>



<a name="loio831d802e8dd440e8a24e0ed0fd393187__section_h3s_1bd_rwb"/>

## Privileges

Requires the MANAGE ANY USER system privilege.



<a name="loio831d802e8dd440e8a24e0ed0fd393187__section_yq3_bbd_rwb"/>

## Examples

This example changes the issue for the X.509 provider MyProvider1.

```
ALTER X509 PROVIDER MyProvider1 SET ISSUER 'CN=DigiCert Global Root CA, O=DigiCert Inc, C=US';
```

This example alters the matching rule for X.509 provider MyProvider1.

```
ALTER X509 PROVIDER MyProvider1 SET MATCHING RULES 'CN=user_*, OU=SAP SE, C=CA';
```

This example removes the matching rules for X.509 provider MyProvider1.

```
ALTER X509 PROVIDER MyProvider UNSET MATCHING RULES;
```

