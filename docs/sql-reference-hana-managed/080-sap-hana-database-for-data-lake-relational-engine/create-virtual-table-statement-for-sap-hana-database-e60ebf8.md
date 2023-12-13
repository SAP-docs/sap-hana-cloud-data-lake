<!-- loioe60ebf8ef9834860ae9e80785499853f -->

# CREATE VIRTUAL TABLE Statement for SAP HANA Database

Creates an SAP HANA database virtual table that points to a remote table for data lake Relational Engine.



## Syntax

```
CREATE VIRTUAL TABLE <virtual_table_name> <table_contents_source> 
    AT <remote_location_clause> WITH REMOTE 
```



<a name="loioe60ebf8ef9834860ae9e80785499853f__section_a5g_r4b_snb"/>

## Syntax Elements


<dl>
<dt><b>

*<table\_contents\_source\>*

</b></dt>
<dd>

Specifies the source from which the table definition is derived.

```
<table_contents_source> ::= ( <table_element> [, <table_element> [, ... ] ] )
```


<dl>
<dt><b>

*<table\_element\>*

</b></dt>
<dd>

Defines the table columns with associated column or table constraints.

```
<table_element> ::=
 <column_definition> [ <column_constraint> ]
```



</dd><dt><b>

*<column\_definition\>*

</b></dt>
<dd>

Defines a table column.

```
<column_definition> ::= <column_name> <data_type> [ <default_value_clause> ]
```


<dl>
<dt><b>

*<column\_name\>*

</b></dt>
<dd>

Specifies the column name.

```
<column_name> ::= <identifier>
```



</dd><dt><b>

*<data\_type\>*

</b></dt>
<dd>

Specifies the column data types.

```
<data_type> ::=
 DATE 
 | TIME 
 | SECONDDATE 
 | TIMESTAMP 
 | TINYINT 
 | SMALLINT 
 | INTEGER 
 | BIGINT 
 | SMALLDECIMAL 
 | REAL 
 | DOUBLE  
 | VARCHAR [ (<unsigned_integer>) ]
 | NVARCHAR [ (<unsigned_integer>) ] 
 | VARBINARY [ (<unsigned_integer>) ] 
 | DECIMAL [ (<unsigned_integer> [, <unsigned_integer> ]) ] 
 | FLOAT [ (<unsigned_integer>) ] 
 | BOOLEAN
```



</dd><dt><b>

*<default\_value\_clause\>*

</b></dt>
<dd>

Specifies a value to be assigned to the column if an INSERT statement does not provide a value for the column.

```
<default_value_clause> ::= DEFAULT <default_value_exp>

<default_value_exp> ::= 
 NULL 
 | <string_literal>
 | <signed_numeric_literal> <unsigned_numeric_literal> 
 | <datetime_value_function>

<datetime_value_function> ::= 
 CURRENT_DATE 
 | CURRENT_TIME 
 | CURRENT_TIMESTAMP 
 | CURRENT_UTCDATE 
 | CURRENT_UTCTIME 
 | CURRENT_UTCTIMESTAMP
```



</dd>
</dl>



</dd><dt><b>

*<column\_constraint\>*

</b></dt>
<dd>

Specifies the column constraint rules.

```
<column_constraint> ::= NULL | NOT NULL | <unique_specification>
```


<dl>
<dt><b>

NULL

</b></dt>
<dd>

Allows NULL values in the column. If NULL is specified it is not considered a constraint, it represents that a column that may contain a null value. The default is NULL.



</dd><dt><b>

NOT NULL

</b></dt>
<dd>

Prohibits NULL values in the column.



</dd><dt><b>

*<unique\_specification\>*

</b></dt>
<dd>

Specifies unique constraints.

```
<unique_specification> ::= UNIQUE | PRIMARY KEY
```


<dl>
<dt><b>

UNIQUE

</b></dt>
<dd>

Specifies a column as a unique key. A composite unique key enables the specification of multiple columns as a unique key. With a unique constraint, multiple rows cannot have the same value in the same column.

A UNIQUE column can contain multiple NULL values.



</dd><dt><b>

PRIMARY KEY

</b></dt>
<dd>

Specifies a primary key constraint, which is a combination of a NOT NULL constraint and a UNIQUE constraint.



</dd>
</dl>



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<remote\_location\_clause\>*

</b></dt>
<dd>

Identifies a table in the data lake Relational Engine. When the WITH REMOTE clause is not specified, this table must already exist. When used with WITH REMOTE, the specified table name becomes the name of the new table.

```
<remote_location_clause> ::= 
   AT "<hana_relational_container_schema>_SOURCE"."NULL"."<relational_container_schema_name>"."<data_lake_table_name>"
```



</dd><dt><b>

WITH REMOTE

</b></dt>
<dd>

Creates a table on the remote source using the *<table\_contents\_source\>* definition and a corresponding virtual table on the local source.



</dd>
</dl>



## Description

The CREATE VIRTUAL TABLE provides a way to access an existing table or view data lake Relational Engine. The list of remote columns is automatically imported into the virtual table.

This syntax is specific to creating an SAP HANA database virtual table in a data lake Relational Engine context. For additional non-data lake Relational Engine specific syntax, see the *CREATE VIRTUAL TABLE Statement \(Data Definition\)* in the *SSAP HANA Cloud, SAP HANA Database SQL Reference Guide*.



<a name="loioe60ebf8ef9834860ae9e80785499853f__section_opr_ddt_5cb"/>

## Permissions

You’ve the CREATE VIRTUAL TABLE object privilege on the SAP HANA database remote source for data lake Relational Engine.



## Examples

This example creates virtual table MY\_HANA\_SCHEMA.V\_T1 that points to the data lake Relational Engine table T1 on the remote source SYSHDL\_CONTAINER1\_SOURCE. Table T1 is in the data lake Relational Engine relational container schema SYSHDL\_CONTAINER1.

```
CREATE VIRTUAL TABLE MY_HANA_SCHEMA.V_T1 AT "SYSHDL_CONTAINER1_SOURCE"."<NULL>"."SYSHDL_CONTAINER1"."T1";
```

This example creates virtual table MY\_HANA\_SCHEMA.V\_T2 and data lake Relational Engine table T2 at the same time. Table T2 has two integer columns \(A, B\) on remote source SYSHDL\_CONTAINER1\_SOURCE in the data lake Relational Engine relational container schema SYSHDL\_CONTAINER1.

```
CREATE VIRTUAL TABLE MY_HANA_SCHEMA.V_T1 (A INT, B INT) AT 
  "SYSHDL_CONTAINER1_SOURCE"."<NULL>"."SYSHDL_CONTAINER1"."T2" WITH REMOTE;
```

**Related Information**  


[ALTER VIRTUAL TABLE Statement for SAP HANA Database](alter-virtual-table-statement-for-sap-hana-database-65ead35.md "Refresh the metadata of an SAP HANA database virtual table that points to a data lake Relational Engine table.")

[DROP VIRTUAL TABLE Statement for SAP HANA Database](drop-virtual-table-statement-for-sap-hana-database-6a7fe7e.md "Removes an SAP HANA database virtual table that points to a data lake Relational Engine table from theSAP HANA database.")

[SAP HANA Cloud, SAP HANA Database SQL Reference Guide](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/cloud/en-US)

