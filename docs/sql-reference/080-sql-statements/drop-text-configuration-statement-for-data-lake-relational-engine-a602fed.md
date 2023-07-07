<!-- loioa602fed184f210158da897dd360ecfd0 -->

# DROP TEXT CONFIGURATION Statement for Data Lake Relational Engine

Drops a text configuration object.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP TEXT CONFIGURATION  [ { <owner> | <schema-name> }.]<text-config-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa602fed184f210158da897dd360ecfd0__IQ_Usage"/>

## Remarks

Use DROP TEXT CONFIGURATION to drop a text configuration object.

Attempting to drop a text configuration object with dependent TEXT indexes results in an error. You must drop the dependent TEXT indexes before dropping the text configuration object.



<a name="loioa602fed184f210158da897dd360ecfd0__IQ_Permissions"/>

## Privileges

Requires one of:

-   You own the text configuration.
-   DROP ANY TEXT CONFIGURATION system privilege
-   DROP ANY OBJECT system privilege
-   DROP object-level privilege on the text configuration
-   DROP object-level privilege on the schema containing the text configuration
-   DROP object-level privilege on the schema containing the text configuration if the schema is owned by another user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioa602fed184f210158da897dd360ecfd0__IQ_Side_Effects"/>

## Side Effects

Automatic commit



<a name="loioa602fed184f210158da897dd360ecfd0__IQ_Examples"/>

## Examples

The following example creates and drops the mytextconfig text configuration object:

```
CREATE TEXT CONFIGURATION mytextconfig FROM default_char;
DROP TEXT CONFIGURATION mytextconfig;
```

**Related Information**  


[ALTER TEXT CONFIGURATION Statement for Data Lake Relational Engine](alter-text-configuration-statement-for-data-lake-relational-engine-a602402.md "Alters a text configuration object.")

[CREATE TEXT CONFIGURATION Statement for Data Lake Relational Engine](create-text-configuration-statement-for-data-lake-relational-engine-a602a06.md "Creates a text configuration object using another text configuration object as a template.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

