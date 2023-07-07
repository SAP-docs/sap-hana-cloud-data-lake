<!-- loioa602711784f21015955aed036a843754 -->

# ALTER TEXT INDEX Statement for Data Lake Relational Engine

Renames, moves or alters the definition of a TEXT index.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER TEXT INDEX [ { <owner> | <schema-name> }.]<text-index-name>
   ON [ { <owner> | <schema-name> }.]<table-name>  
   RENAME { AS | TO } <new-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa602711784f21015955aed036a843754__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

RENAME

</b></dt>
<dd>

Renames the TEXT index.



</dd>
</dl>



<a name="loioa602711784f21015955aed036a843754__IQ_Permissions"/>

## Privileges

Requires one of:

-   You own the underlying table of the index.
-   ALTER ANY INDEX system privilege
-   ALTER ANY OBJECT system privilege
-   ALTER object-level privilege on the table.
-   REFERENCES object-level privilege on the table.
-   ALTER or REFERENCES object-level privilege on the schema containing the table if the schema is owned by another user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioa602711784f21015955aed036a843754__IQ_Side_Effects"/>

## Side Effects

Automatic commit



<a name="loioa602711784f21015955aed036a843754__IQ_Examples"/>

## Examples

The following example creates a TEXT index, `MyTextIndex`, defining it as IMMEDIATE REFRESH, rename the TEXT index to `Text_index_daily`, and move the TEXT index to a dbspace named `tispace`:

```
CREATE TEXT INDEX MyTextIndex ON Customers ( CompanyName ) IMMEDIATE REFRESH;
ALTER TEXT INDEX MyTextIndex ON Customers RENAME AS Text_index_daily;
ALTER TEXT INDEX Text_Index_Daily ON Customers MOVE TO tispace;
```

**Related Information**  


[CREATE TEXT INDEX Statement for Data Lake Relational Engine](create-text-index-statement-for-data-lake-relational-engine-a602ced.md "Creates a TEXT index and specifies the text configuration object to use.")

[DROP TEXT INDEX Statement for Data Lake Relational Engine](drop-text-index-statement-for-data-lake-relational-engine-a60331d.md "Removes a TEXT index from the database.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

