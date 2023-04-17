<!-- loio06e06d8484ab4d97bfd83494bbcf8e06 -->

# REVOKE JWT LOGIN Statement for Data Lake Relational Engine

Removes mappings between external identities from a JWT provider and a user in the data lake Relational Engine database.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
REVOKE JWT LOGIN FROM <external_identity> [, ...] 
   FOR PROVIDER <jwt_provider_name>
```



<a name="loio06e06d8484ab4d97bfd83494bbcf8e06__IQ_Parameters"/>

## Parameters

 *<external\_identity\>*
 :   Specifies the external identity to map to the data lake Relational Engine user.

    ```
    <external_identity> ::= <simple_identifier>
    ```

  *<jwt\_provider\_name\>*
 :   Specifies the JWT provider with external identities to unmap from the user.

    ```
    <jwt_provider_name> ::= <simple_identifier>
    ```

 

<a name="loio06e06d8484ab4d97bfd83494bbcf8e06__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY USER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md).



<a name="loio06e06d8484ab4d97bfd83494bbcf8e06__section_gwx_f3p_p4b"/>

## Example

```
REVOKE JWT LOGIN FROM SQLTester FOR PROVIDER my_jwt_provider
```

**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

