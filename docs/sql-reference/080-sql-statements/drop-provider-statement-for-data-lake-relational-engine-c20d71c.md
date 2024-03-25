<!-- loioc20d71c4c669410780a5cab922e71c5d -->

# DROP PROVIDER Statement for Data Lake Relational Engine

Drops a JWT or x509 provider from the data lake Relational Engine database.



<a name="loioc20d71c4c669410780a5cab922e71c5d__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP { JWT | x509 } PROVIDER <provider_name> [ CASCADE ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioc20d71c4c669410780a5cab922e71c5d__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<provider\_name\>*

</b></dt>
<dd>

Specifies the identifier of a provider to drop.

```
<provider_name> ::= <simple_identifier>;
```



</dd><dt><b>

CASCADE

</b></dt>
<dd>

Removes all mappings that reference the provider. If not specified, then the drop fails if there are any certificates that reference the provider or if a user is mapped to the provider.

Use the SYSCERTIFICATE system view to check for certificates referencing a provider. Use the SYSJWTLOGINMAP or SYSX509LOGINMAP system views to check for users mapped to a provider.



</dd>
</dl>



<a name="loioc20d71c4c669410780a5cab922e71c5d__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY USER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md).



<a name="loioc20d71c4c669410780a5cab922e71c5d__section_gwx_f3p_p4b"/>

## Example

This example drops the JWT provider myjwtprovider1.

```
DROP JWT PROVIDER myjwtprovider1;
```

This example drops the X.509 provider myx509provider2.

```
DROP X509 PROVIDER myx509provider2;
```

**Related Information**  


[CREATE JWT PROVIDER Statement for Data Lake Relational Engine](create-jwt-provider-statement-for-data-lake-relational-engine-49b7ee1.md "Defines a JWT provider in the data lake Relational Engine database.")

[CREATE X509 PROVIDER Statement for Data Lake Relational Engine](create-x509-provider-statement-for-data-lake-relational-engine-fe6ef48.md "Create an X.509 provider in the database.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[X.509 Certificate-Based User Authentication](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_1_QRC/en-US/c9bf672bbc2849568a1ff1d2fbc9a78d.html "Data lake Relational Engine supports X.509 client certificates for user authentication.") :arrow_upper_right:

