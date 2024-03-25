<!-- loio582d22d53e994855a9c7fa7b9a3fda25 -->

# GRANT JWT LOGIN Statement for Data Lake Relational Engine

Maps one or more external identities from a JWT provider to a user in the data lake Relational Engine database.



<a name="loio582d22d53e994855a9c7fa7b9a3fda25__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
GRANT JWT LOGIN TO <external_identity> FOR PROVIDER <jwt_provider_name> AS USER <userid>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio582d22d53e994855a9c7fa7b9a3fda25__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<external\_identity\>*

</b></dt>
<dd>

Specifies the external identity to map to the data lake Relational Engine user.

```
<external_identity> ::= <simple_identifier>;
```



</dd><dt><b>

*<jwt\_provider\_name\>*

</b></dt>
<dd>

Specifies the JWT provider.

```
<jwt_provider_name> ::= <simple_identifier>;
```



</dd><dt><b>

*<userid\>*

</b></dt>
<dd>

Specifies the data lake Relational Engine user to which the external identities are mapped.

```
<userid> ::= <simple_identifier>;
```



</dd>
</dl>



<a name="loio582d22d53e994855a9c7fa7b9a3fda25__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY USER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md).



<a name="loio582d22d53e994855a9c7fa7b9a3fda25__section_gwx_f3p_p4b"/>

## Example

```
GRANT JWT LOGIN TO external_user FOR PROVIDER my_jwt_provider AS USER HDLUSER;
```

**Related Information**  


[REVOKE JWT LOGIN Statement for Data Lake Relational Engine](revoke-jwt-login-statement-for-data-lake-relational-engine-06e06d8.md "Removes mappings between external identities from a JWT provider and a user in the data lake Relational Engine database.")

