<!-- loio582d22d53e994855a9c7fa7b9a3fda25 -->

# GRANT JWT LOGIN Statement for Data Lake Relational Engine

Maps one or more external identities from a JWT provider to a user in the data lake Relational Engine database.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
GRANT JWT LOGIN TO <external_identity> FOR PROVIDER <jwt_provider_name> AS USER <userid>
```



<a name="loio582d22d53e994855a9c7fa7b9a3fda25__IQ_Parameters"/>

## Parameters

 *<external\_identity\>*
 :   Specifies the external identity to map to the data lake Relational Engine user.

    ```
    <external_identity> ::= <simple_identifier>
    ```

  *<jwt\_provider\_name\>*
 :   Specifies the JWT provider.

    ```
    <jwt_provider_name> ::= <simple_identifier>
    ```

  *<userid\>*
 :   Specifies the data lake Relational Engine user to which the external identities are mapped.

    ```
    <userid> ::= <simple_identifier>
    ```

 

<a name="loio582d22d53e994855a9c7fa7b9a3fda25__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY USER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md).



<a name="loio582d22d53e994855a9c7fa7b9a3fda25__section_gwx_f3p_p4b"/>

## Example

```
GRANT JWT LOGIN TO external_user FOR PROVIDER my_jwt_provider AS USER HDLUSER
```

**Related Information**  


[REVOKE JWT LOGIN Statement for Data Lake Relational Engine](revoke-jwt-login-statement-for-data-lake-relational-engine-06e06d8.md "Removes mappings between external identities from a JWT provider and a user in the data lake Relational Engine database.")

