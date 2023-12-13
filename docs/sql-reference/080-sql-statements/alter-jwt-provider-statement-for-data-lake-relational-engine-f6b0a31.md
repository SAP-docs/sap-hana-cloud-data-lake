<!-- loiof6b0a31d00884412a259cea30ee39b8f -->

# ALTER JWT PROVIDER Statement for Data Lake Relational Engine

Alters a JWT provider in the data lake Relational Engine database.



<a name="loiof6b0a31d00884412a259cea30ee39b8f__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER JWT PROVIDER <jwt_provider_name>
    { SET { <issuer_clause> | <claims_clause> | <priority_clause> }
      | UNSET <unset_claims_clause> };
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



## Parameters


<dl>
<dt><b>

*<jwt\_provider\_name\>*

</b></dt>
<dd>

Specifies the identifier of a JWT provider to be modified.

```
<jwt_provider_name> ::= <simple_identifier>
```



</dd><dt><b>

*<issuer\_clause\>*

</b></dt>
<dd>

Specifies the issuer name. Tokens with an "iss" claim matching this name are mapped to this JWT provider.

```
<issuer_clause> ::= WITH ISSUER <sting_literal>;
```



</dd><dt><b>

*<claims\_clause\>*

</b></dt>
<dd>

```
<claims_clause> ::= 
   { <external_id_clause> | <claim_compare_clause> } [ <claims_clause> ];
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
<claim_compare_clause> ::= { <claim_equals_clause> | <claim_has_member_clause> };
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
<claim_value> ::= <string_literal>;
```



</dd><dt><b>

*<claim\_has\_member\_clause\>*

</b></dt>
<dd>

*<claim\_equals\_clause\>* expects the JWT claim to be an array of strings. If the JWT contains a simple string instead of an array of strings, then the simple string is treated like an array with one entry.

```
<claim_has_member_clause> ::= CLAIM <claim_name> HAS MEMBER <claim_value>

<claim_name> ::= <string_literal>
<claim_value> ::= <string_literal>;
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
<priority_clause> ::= PRIORITY <number>;
```

*<number\>* is a value between 1-250.

Providers with the same issuer must have different priorities. During authentication, the provider with the highest priority is checked first. If the claims match with the provided JWT token, that provider is used for the authentication; otherwise, the provider with the next lower priority is tested until a match is found.



</dd><dt><b>

*<unset\_claims\_clause\>*

</b></dt>
<dd>

Unsets one or more claims. You cannot unset the *<external\_id\_clause\>*. If an external id claim is set using *<claim\_compare\_clause\>*, that claim can be unset successfully.

```
CLAIM <claim_name> [<unset_claims_clause>];
```



</dd>
</dl>



<a name="loiof6b0a31d00884412a259cea30ee39b8f__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY USER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md).



<a name="loiof6b0a31d00884412a259cea30ee39b8f__section_gwx_f3p_p4b"/>

## Examples

-   The following example alters the issuer for `my_jwt_provider`:Requires the MANAGE ANY USER system privilege. See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md).

    ```
    ALTER JWT PROVIDER my_jwt_provider SET ISSUER 'http://test.localhost:8080/uaa/oauth/token';
    ```

-   The following example alters the external identity claim for `my_jwt_provider`:

    ```
    ALTER JWT PROVIDER my_jwt_provider SET CLAIM 'user_name' AS EXTERNAL IDENTITY;
    ```

-   The following example sets two claims for `my_jwt_provider`:

    ```
    ALTER JWT PROVIDER my_jwt_provider 
    	SET CLAIM 'origin' = 'http://example.com/'
    	CLAIM 'aud' HAS MEMBER 'app1';
    ```

-   The following example unsets two claims for `my_jwt_provider`:

    ```
    ALTER JWT PROVIDER my_jwt_provider UNSET CLAIM 'origin' CLAIM 'aud';
    ```


**Related Information**  


[CREATE JWT PROVIDER Statement for Data Lake Relational Engine](create-jwt-provider-statement-for-data-lake-relational-engine-49b7ee1.md "Defines a JWT provider in the data lake Relational Engine database.")

[SYSJWTLOGINMAP System View for Data Lake Relational Engine](../070-system-and-monitoring-views/sysjwtloginmap-system-view-for-data-lake-relational-engine-d5978ec.md "Lists the JWT-user mappings configured in the data lake Relational Engine database. The underlying system table for this view is ISYSJWTLOGINMAP.")

[SYSJWTPROVIDERS System View for Data Lake Relational Engine](../070-system-and-monitoring-views/sysjwtproviders-system-view-for-data-lake-relational-engine-40fe6b4.md "Lists JWT providers configured in the data lake Relational Engine database. The underlying system table for this view is ISYSJWTPROVIDERS.")

[SYSJWTPROVIDERCMPCLAIMS System View for Data Lake Relational Engine](../070-system-and-monitoring-views/sysjwtprovidercmpclaims-system-view-for-data-lake-relational-engine-765761f.md "Lists claims set in JWT providers. The underlying system table for this view is ISYSJWTPROVIDERCMPCLAIMS.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[DROP PROVIDER Statement for Data Lake Relational Engine](drop-provider-statement-for-data-lake-relational-engine-c20d71c.md "Drops a JWT or x509 provider from the data lake Relational Engine database.")

