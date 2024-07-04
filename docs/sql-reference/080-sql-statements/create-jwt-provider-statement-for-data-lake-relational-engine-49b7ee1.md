<!-- loio49b7ee108b7b40f880f936b940e2b037 -->

# CREATE JWT PROVIDER Statement for Data Lake Relational Engine

Defines a JWT provider in the data lake Relational Engine database.



<a name="loio49b7ee108b7b40f880f936b940e2b037__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE JWT PROVIDER <jwt_provider_name> <issuer_clause> <claims_clause> [ <priority_clause> ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio49b7ee108b7b40f880f936b940e2b037__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<jwt\_provider\_name\>*

</b></dt>
<dd>

Specifies the identifier of a JWT provider to be created. The JWT provider name must not already be defined.

```
<jwt_provider_name> ::= <simple_identifier>
```



</dd><dt><b>

*<issuer\_clause\>*

</b></dt>
<dd>

Specifies the issuer name. Tokens with an "iss" claim matching this name are mapped to this JWT provider.

```
<issuer_clause> ::= WITH ISSUER <sting_literal>
```



</dd><dt><b>

*<claims\_clause\>*

</b></dt>
<dd>

```
<claims_clause> ::= 
   { <external_id_clause> | <claim_compare_clause> } [...]
```


<dl>
<dt><b>

*<external\_id\_clause\>*

</b></dt>
<dd>

Adds a claim that must be verified in JWT token which represents external identity. It can be modified using ALTER JWT PROVIDER but cannot be deleted.

```
<external_id_clause> ::= CLAIM <string_literal> AS EXTERNAL IDENTITY
```



</dd><dt><b>

*<claim\_compare\_clause\>*

</b></dt>
<dd>

A claim can only be used for one compare operation, either = or HAS MEMBER. Claim and value comparisons are case-sensitive.

```
<claim_compare_clause> ::= { <claim_equals_clause> | <claim_has_member_clause> }
```


<dl>
<dt><b>

*<claim\_equals\_clause\>*

</b></dt>
<dd>

*<claim\_equals\_clause\>* expects the JWT claim value to be a string or array of strings and the value must exactly match the configured value \(for example, 'origin' claim or 'zone\_uuid' claim\).

```
<claim_equals_clause> ::= CLAIM <claim_name> = <claim_value>

<claim_name> ::= <string_literal>
<claim_value> ::= <string_literal>
```



</dd><dt><b>

*<claim\_has\_member\_clause\>*

</b></dt>
<dd>

*<claim\_equals\_clause\>* expects the JWT claim to be an array of strings. If the JWT contains a simple string instead of an array of strings, then the simple string is treated like an array with one entry.

```
<claim_has_member_clause> ::= CLAIM <claim_name> HAS MEMBER <claim_value>

<claim_name> ::= <string_literal>
<claim_value> ::= <string_literal>
```



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<priority\_clause\>*

</b></dt>
<dd>

Sets priority for a provider entry to allow existence of multiple providers with the same issuer. The default value is 100.

```
<priority_clause> ::= PRIORITY <number>
```

*<number\>* is a value between 1-250.

Providers with the same issuer must have different priorities. During authentication, the provider with the highest priority is checked first. If the claims match with the provided JWT token, that provider is used for the authentication; otherwise, the provider with the next lower priority is tested until a match is found.



</dd>
</dl>



## Privileges

Requires the MANAGE ANY USER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md).



<a name="loio49b7ee108b7b40f880f936b940e2b037__section_gwx_f3p_p4b"/>

## Examples

```
CREATE JWT PROVIDER my_jwt_provider WITH ISSUER 'http://example.com:8080/uaa/oauth/token' 
 CLAIM 'sub' AS EXTERNAL IDENTITY
 CLAIM 'origin' = 'http://example.com/'
 CLAIM 'aud' HAS MEMBER 'app1';
```

**Related Information**  


[JSON Web Token User Authentication](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_3_QRC/en-US/90d07ffd877e4b3db69b66c2e585e2e0.html "Data lake Relational Engine supports JSON Web Tokens (JWT) for user authentication.") :arrow_upper_right:

[ALTER JWT PROVIDER Statement for Data Lake Relational Engine](alter-jwt-provider-statement-for-data-lake-relational-engine-f6b0a31.md "Alters a JWT provider in the data lake Relational Engine database.")

[SYSJWTLOGINMAP System View for Data Lake Relational Engine](../070-system-and-monitoring-views/sysjwtloginmap-system-view-for-data-lake-relational-engine-d5978ec.md "Lists the JWT-user mappings configured in the data lake Relational Engine database. The underlying system table for this view is ISYSJWTLOGINMAP.")

[SYSJWTPROVIDERS System View for Data Lake Relational Engine](../070-system-and-monitoring-views/sysjwtproviders-system-view-for-data-lake-relational-engine-40fe6b4.md "Lists JWT providers configured in the data lake Relational Engine database. The underlying system table for this view is ISYSJWTPROVIDERS.")

[SYSJWTPROVIDERCMPCLAIMS System View for Data Lake Relational Engine](../070-system-and-monitoring-views/sysjwtprovidercmpclaims-system-view-for-data-lake-relational-engine-765761f.md "Lists claims set in JWT providers. The underlying system table for this view is ISYSJWTPROVIDERCMPCLAIMS.")

[DROP PROVIDER Statement for Data Lake Relational Engine](drop-provider-statement-for-data-lake-relational-engine-c20d71c.md "Drops a JWT or x509 provider from the data lake Relational Engine database.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

