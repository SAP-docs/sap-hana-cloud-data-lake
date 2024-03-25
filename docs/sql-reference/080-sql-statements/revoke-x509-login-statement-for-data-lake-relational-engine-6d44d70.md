<!-- loio6d44d706974542d6832c180c5198ec4c -->

# REVOKE X509 LOGIN Statement for Data Lake Relational Engine

Removes mappings between external identities from user certificates and a data lake Relational Engine user through the X509 Provider.



<a name="loio6d44d706974542d6832c180c5198ec4c__section_xv3_wvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
REVOKE X509 LOGIN FROM [ ( { <external_identity> [, ...] | ANY AS USER <userid> [, ...] } ) ] FOR PROVIDER <x509_provider_name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio6d44d706974542d6832c180c5198ec4c__section_sfn_kbd_rwb"/>

## Parameters


<dl>
<dt><b>

*<external\_identity\>*

</b></dt>
<dd>

Specifies the external identity that was used to map to a data lake Relational Engine user.

```
<external_identity> ::= <string_literal>;
```



</dd><dt><b>

*<userid\>*

</b></dt>
<dd>

Specifies the existing data lake Relational Engine user to remove X.509 mappings from.

```
<userid> ::= <simple_identifier>;
```



</dd><dt><b>

*<x509\_provider\_name\>*

</b></dt>
<dd>

Specifies the existing X.509 provider to unmap from the user.

```
<x509_provider_name> ::= <simple_identifier>;
```



</dd>
</dl>



<a name="loio6d44d706974542d6832c180c5198ec4c__section_h3s_1bd_rwb"/>

## Privileges

Requires the MANAGE ANY USER system privilege.



<a name="loio6d44d706974542d6832c180c5198ec4c__section_yq3_bbd_rwb"/>

## Examples

This example removes the external identity mapped to user1 for provider MyProvider1.

```
REVOKE X509 LOGIN FROM 'CN=JOHN, OU=SAP SE, C=CA' FOR PROVIDER MyProvider;
```

This example removes all external identities mapped to user1 for provider MyProvider1.

```
REVOKE X509 LOGIN FROM ANY AS USER user1 FOR PROVIDER MyProvider;
```

