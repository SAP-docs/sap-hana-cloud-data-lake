<!-- loio819f6ce2e6ef4d78ba11c7fcc194ea6e -->

# SET SCHEMA Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Sets the default schema for the connection



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).



```
SET SCHEMA [ <schema_name> ]
```



<a name="loio819f6ce2e6ef4d78ba11c7fcc194ea6e__section_hgp_pjr_btb"/>

## Remarks

When executing a SQL statement that references a database object, if a schema name is not specified, then the current value of the SET SCHEMA statement is cleared. The SET schema remains in effect for the duration of the connection or until reset to another schema name or cleared.



<a name="loio819f6ce2e6ef4d78ba11c7fcc194ea6e__section_erw_syy_wwb"/>

## Privileges



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio819f6ce2e6ef4d78ba11c7fcc194ea6e__section_bft_rjr_btb"/>

## Example

The following example creates a new schema called SCHEMA\_1, and then sets the default schema to it.

```
CREATE SCHEMA SCHEMA1;
```

```
SET SCHEMA SCHEMA1;
```

Table T1 is then created without specifying a schema.

```
CREATE T1 (A INT, B INT);
```

The table is created in the default \(SET\) schema. To query table T1, the following two statements are equivalent:

```
SELECT * FROM T1;
```

```
SELECT * FROM SCHEMA_1.T1;
```

This clears the current SET SCHEMA value in effect, SCHEMA1.

```
SET SCHEMA;
```
