<!-- loiob23679a94d9f45a4b169f484005f46da -->

# SET SCHEMA Statement for Data Lake Relational Engine

Sets the default schema for the connection



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
SET SCHEMA [ <schema_name> ]
```



<a name="loiob23679a94d9f45a4b169f484005f46da__set_schema_remarks1"/>

## Remarks

When executing a SQL statement that references a database object, if a schema name is not specified, then the current value of the SET SCHEMA statement is cleared. The SET schema remains in effect for the duration of the connection or until reset to another schema name or cleared.



<a name="loiob23679a94d9f45a4b169f484005f46da__set_schema_privileges1"/>

## Privileges



### 

None



<a name="loiob23679a94d9f45a4b169f484005f46da__set_schema_example1"/>

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

