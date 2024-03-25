<!-- loioa60331d484f21015b12ac440f67fd4d1 -->

# DROP TEXT INDEX Statement for Data Lake Relational Engine

Removes a TEXT index from the database.



<a name="loioa60331d484f21015b12ac440f67fd4d1__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP TEXT INDEX <text-index-name>
   ON [ { <owner> | <schema-name> }.]<table-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa60331d484f21015b12ac440f67fd4d1__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

ON

</b></dt>
<dd>

Specifies the table on which the TEXT index is built.



</dd>
</dl>



<a name="loioa60331d484f21015b12ac440f67fd4d1__IQ_Usage"/>

## Remarks

You must drop dependent TEXT indexes before you can drop a text configuration object.



<a name="loioa60331d484f21015b12ac440f67fd4d1__IQ_Permissions"/>

## Privileges

-   Requires one of:
    -   You own the underlying table of the index.
    -   DROP ANY INDEX system privilege
    -   DROP ANY OBJECT system privilege
    -   REFERENCES or DROP object-level privilege on the underlying table of the index.
    -   REFERENCES object-level privilege on the schema containing the underlying table of the index if the schema is owned by another user.


See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioa60331d484f21015b12ac440f67fd4d1__IQ_Side_Effects"/>

## Side Effects

Automatic commit



<a name="loioa60331d484f21015b12ac440f67fd4d1__IQ_Examples"/>

## Examples

The following example creates and drops the `TextIdx` TEXT index:

```
CREATE TEXT INDEX TextIdx ON Customers ( Street );
DROP TEXT INDEX TextIdx ON Customers;
```

**Related Information**  


[ALTER TEXT INDEX Statement for Data Lake Relational Engine](alter-text-index-statement-for-data-lake-relational-engine-a602711.md "Renames, moves or alters the definition of a TEXT index.")

[CREATE TEXT INDEX Statement for Data Lake Relational Engine](create-text-index-statement-for-data-lake-relational-engine-a602ced.md "Creates a TEXT index and specifies the text configuration object to use.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

