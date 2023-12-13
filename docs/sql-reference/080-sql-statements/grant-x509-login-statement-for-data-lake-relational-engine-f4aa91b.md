<!-- loiof4aa91b2fcd44656927bb92fbc2980d4 -->

# GRANT X509 LOGIN Statement for Data Lake Relational Engine

Maps one or more mappings between external identities from user certificates and a data lake Relational Engine user through the X509 Provider.



<a name="loiof4aa91b2fcd44656927bb92fbc2980d4__section_xv3_wvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
GRANT X509 LOGIN TO { <external_identity> | ANY } FOR PROVIDER <x509_provider_name> AS USER <userid>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiof4aa91b2fcd44656927bb92fbc2980d4__section_ec3_kbd_rwb"/>

## Parameters


<dl>
<dt><b>

*<external\_identity\>*

</b></dt>
<dd>

Specifies the external identity to map to the data lake Relational Engine user.

```
<external_identity> ::= <string_literal>;
```



</dd><dt><b>

*<x509\_provider\_name\>*

</b></dt>
<dd>

Specifies the existing X.509 provider to use for authentication.

```
<x509_provider_name> ::= <simple_identifier>;
```



</dd><dt><b>

*<userid\>*

</b></dt>
<dd>

Specifies the existing data lake Relational Engine user to which the external identities are mapped.

```
<userid> ::= <simple_identifier>;
```



</dd>
</dl>



<a name="loiof4aa91b2fcd44656927bb92fbc2980d4__section_h3s_1bd_rwb"/>

## Privileges

Requires the MANAGE ANY USER system privilege.



<a name="loiof4aa91b2fcd44656927bb92fbc2980d4__section_yq3_bbd_rwb"/>

## Examples

This example allows user1 to log on using the X.509 authentication provider MyProvider1.

```
GRANT X509 LOGIN TO 'CN=JOHN, OU=SAP SE, C=CA' FOR PROVIDER MyProvider1 AS USER user1;
```

