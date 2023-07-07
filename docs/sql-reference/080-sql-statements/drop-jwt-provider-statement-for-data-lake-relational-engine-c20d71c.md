<!-- loioc20d71c4c669410780a5cab922e71c5d -->

# DROP JWT PROVIDER Statement for Data Lake Relational Engine

Drops a JWT provider from the data lake Relational Engine database.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP JWT PROVIDER <jwt_provider_name> [ CASCADE ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioc20d71c4c669410780a5cab922e71c5d__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<jwt\_provider\_name\>*

</b></dt>
<dd>

Specifies the identifier of a JWT provider to drop.

```
<jwt_provider_name> ::= <simple_identifier>
```



</dd><dt><b>

CASCADE

</b></dt>
<dd>

Removes all mappings that reference the provider.



</dd>
</dl>



<a name="loioc20d71c4c669410780a5cab922e71c5d__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY USER system privilege.



See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md).



<a name="loioc20d71c4c669410780a5cab922e71c5d__section_gwx_f3p_p4b"/>

## Example

```
DROP JWT PROVIDER my_jwt_provider
```

**Related Information**  


[CREATE JWT PROVIDER Statement for Data Lake Relational Engine](create-jwt-provider-statement-for-data-lake-relational-engine-49b7ee1.md "Defines a JWT provider in the data lake Relational Engine database.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

