<!-- loioa3bd7356d0c1420596b03576520406fe -->

# DROP X509 PROVIDER Statement for Data Lake Relational Engine

Drop an X.509 provider in the database.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP X509 PROVIDER <x509_provider_name> [ CASCADE ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa3bd7356d0c1420596b03576520406fe__section_vjd_kbd_rwb"/>

## Parameters


<dl>
<dt><b>

*<x509\_provider\_name\>*

</b></dt>
<dd>

Specifies an existing X.509 provider to drop.

```
<x509_provider_name> ::= <simple_identifier>
```



</dd><dt><b>

CASCADE

</b></dt>
<dd>

Removes all mappings that reference the provider. If not specified, then the drop fails if there are any certificates that reference the provider \(SYSCERTIFICATE system view\) or if a user is mapped to the provider \(SYSX509LOGINMAP system view\).



</dd>
</dl>



<a name="loioa3bd7356d0c1420596b03576520406fe__section_h3s_1bd_rwb"/>

## Privileges

Requires the MANAGE ANY USER system privilege.



<a name="loioa3bd7356d0c1420596b03576520406fe__section_yq3_bbd_rwb"/>

## Examples

This example drops the X.509 provider MyProvider1.

```
DROP X509 PROVIDER MyProvider1;
```

