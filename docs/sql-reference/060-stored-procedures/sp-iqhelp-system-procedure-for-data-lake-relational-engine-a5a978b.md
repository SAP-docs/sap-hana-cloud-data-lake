<!-- loioa5a978bb84f21015ae55ee5c09228875 -->

# sp\_iqhelp System Procedure for Data Lake Relational Engine

Displays information about system and user-defined objects and data types.



<a name="loioa5a978bb84f21015ae55ee5c09228875__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqhelp [ <obj-name> [, <obj-owner> [, <obj-category>
   [, <obj-type> ] ] ] ]
```



<a name="loioa5a978bb84f21015ae55ee5c09228875__iq_refbb_1577"/>

## Parameters


<dl>
<dt><b>

*<obj-name\>* 

</b></dt>
<dd>

The name of the object.



</dd><dt><b>

*<obj-owner\>*

</b></dt>
<dd>

The owner of the object.



</dd><dt><b>

*<obj-category\>*

</b></dt>
<dd>

\(Optional\) A parameter that specifies the category of the object.

Columns, constraints, and indexes are associated with tables and cannot be queried directly. When a table is queried, the information about columns, indexes, and constraints associated with that table is displayed.

If the specified object category is not one of the allowed values, displays an ***Invalid object category*** message.

Allowed values are:

-   table – object is a base table
-   view – object is a view
-   procedure – object is a stored procedure or function
-   event – object is an event
-   datatype – object is a system or user-defined data type



</dd><dt><b>

*<obj-type\>*

</b></dt>
<dd>

The type of object. Allowed values are:

-   SYSTEM – displays information about system objects \(objects owned by user SYS or dbo\) only
-   ALL – displays information about all objects. By default, only information about non-system objects is displayed. If the specified object type is not SYSTEM or ALL, displays an ***Invalid object type*** message.



</dd>
</dl>

The sp\_iqhelp procedure can be invoked without any parameters. If no parameters are specified, sp\_iqhelp displays information about all independent objects in the database, that is, base tables, views, stored procedures, functions, events, and data types.



<a name="loioa5a978bb84f21015ae55ee5c09228875__section_ohf_b4b_vzb"/>

## Result Set

The result set depends on the parameters specified.



<a name="loioa5a978bb84f21015ae55ee5c09228875__section_wkt_4hz_mbb"/>

## Remarks

If you do not specify any of the first three parameters, but specify the next parameter in the sequence, you must substitute NULL for the omitted parameters. For example, sp\_iqhelp NULL, NULL, NULL, SYSTEM and `sp_iqhelp NULL, user1, "table"`.

Enclose the *<obj-category\>* parameter in single or double quotes., except when NULL.

If sp\_iqhelp does not find an object in the database that satisfies the specified description, displays a ***No object found for the given description*** message.

The sp\_iqhelp stored procedure displays information about system and user-defined objects and data types in an IQ database. Objects supported by sp\_iqhelp are tables, views, columns, indexes, constraints, stored procedures, functions, events, and data types.

If you specify one or more parameters, the result is filtered by the specified parameters. For example, if *<obj-name\>* is specified, only information about the specified object is displayed. If *<obj-owner\>* is specified, sp\_iqhelp returns information only about objects owned by the specified owner. If no parameters are specified, `sp_iqhelp` displays summary information about all user-defined tables, views, procedures, events, and data types in the database.

The sp\_iqhelp procedure returns either summary or detailed information, depending on whether the specified parameters match multiple objects or a single object. The output columns of sp\_iqhelp are similar to the columns displayed by the stored procedures sp\_iqtable, sp\_iqindex, sp\_iqview, and sp\_iqconstraint.

When multiple objects match the specified sp\_iqhelp parameters, sp\_iqhelp displays summary information about those objects. Object types and the columns displayed are:

-   Base table – table\_name, table\_owner, server\_type, location, table\_constraints, remarks
-   View – view\_name, view\_creator, view\_def, server\_type, location, remarks
-   Stored procedure – proc\_name, proc\_creator, proc\_defn, replicate, srvid, remarks
-   Function – proc\_name, proc\_creator, proc\_defn, replicate, remarks
-   Event – event\_name, event\_creator, enabled, location, event\_type, action, external\_action, condition, remarks
-   System and user-defined data types – type\_name, creator, nulls, width, scale, default, check

When a single object matches the specified sp\_iqhelp parameters, sp\_iqhelp displays detailed information about the object:


<table>
<tr>
<th valign="top">

Object Type

</th>
<th valign="top">

Description

</th>
<th valign="top">

Columns

</th>
</tr>
<tr>
<td valign="top">

Table

</td>
<td valign="top">

Displays information about the specified base table, its columns, indexes, and constraints.

</td>
<td valign="top">

-   Table columns: table\_name, table\_owner, server\_type, location, table\_constraints, remarks
-   Column columns: column\_name, domain\_name, width, scale, nulls, default, check, pkey, user\_type, cardinality, est\_cardinality, remarks
-   Index columns: index\_name, column\_name, index\_type, unique\_index, location, remarks
-   Constraint columns: constraint\_name \(role\), column\_name, index\_name, constraint\_type, foreigntable\_name, foreigntable\_owner, foreigncolumn\_name, foreignindex\_name, location



</td>
</tr>
<tr>
<td valign="top">

View

</td>
<td valign="top">

Displays information about the specified view and its columns

</td>
<td valign="top">

-   View columns: view\_name, view\_creator, view\_def, server\_type, location, remarks
-   Column columns: column\_name, domain\_name, width, scale, nulls, default, check, pkey, user\_type, cardinality, est\_cardinality, remarks



</td>
</tr>
<tr>
<td valign="top">

Stored procedure

</td>
<td valign="top">

Displays information about the specified procedure and its parameters

</td>
<td valign="top">

-   Procedure columns: proc\_name, proc\_creator, proc\_defn, replicate, srvid, remarks
-   Parameter columns: parameter\_name, type, width, scale, default, mode



</td>
</tr>
<tr>
<td valign="top">

Function

</td>
<td valign="top">

Displays information about the specified function and its parameters

</td>
<td valign="top">

-   Function columns: proc\_name, proc\_creator, proc\_defn, replicate, srvid, remarks
-   Parameter columns: parameter\_name, type, width, scale, default, mode



</td>
</tr>
<tr>
<td valign="top">

Event

</td>
<td valign="top">

Displays information about the specified event

</td>
<td valign="top">

-   Event columns: event\_name, event\_creator, enabled, location, event\_type, action, external\_action, condition, remarks



</td>
</tr>
<tr>
<td valign="top">

Data type

</td>
<td valign="top">

Displays information about the specified data type

</td>
<td valign="top">

-   Data type columns: type\_name, creator, nulls, width, scale, default, check



</td>
</tr>
</table>

> ### Note:  
> Procedure definitions \(proc-defn\) of system procedures are encrypted and hidden from view.

For descriptions of the individual output columns, refer to the related stored procedure. For example, for a description of the table column, see the sp\_iqtable procedure.



<a name="loioa5a978bb84f21015ae55ee5c09228875__iq_refbb_1576"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.



<a name="loioa5a978bb84f21015ae55ee5c09228875__section_dgt_mkz_mbb"/>

## Side Effects

None



<a name="loioa5a978bb84f21015ae55ee5c09228875__iq_refbb_1583"/>

## Examples

This example returns detailed information about the table sale in SALE tables:

```
CALL sp_iqhelp SALE;
```

```

f1                     f2           f3           f4           f5           f6             f7           f8                 f9           f10         f11

Table_name             Table_owner  Server_type  Location     dbspace_id   isPartitioned  Remarks      table_constraints  
==========             ===========  ===========  ===========  ===========  ===========    ===========  ===========
Z2                     HDLADMIN     IQ           Main         16388        N              NULL         NULL

column_name            domain_name  width        scale        nulls        [default]      cardinality  isPartitioned      remarks      [check]   
==========             ===========  ===========  ===========  ===========  ===========    ===========  ===========        ===========  ===========  ===========	
a                      integer      4            0            Y            NULL           0            N                  NULL         NULL
b_date                 datetimex    8            0            Y            NULL           0            N                  NULL         NULL
											
index_name             column_name  index_type  unique_index  location     remarks
==========             ===========  ===========  ===========  ===========  ===========
ASIQ_IDX_T1743_C1_FP   a            FP           N            Main         NULL
ASIQ_IDX_T1743_C2_FP   b_date       FP           N            Main         NULL
```

This example returns summary information about all user-defined tables, views, procedures, events, and data types in the database:

```
CALL sp_iqhelp;
```

This example returns information about table t1 owned by user u1 and the columns, indexes, and constraints associated with t1:

```
CALL sp_iqhelp t1, u1, "table";
```

This example returns information about view v1u1 and the columns associated with v1:

```
CALL sp_iqhelp NULL, u1, "view";
```

This example returns information about the procedure sp2 and the parameters of owned by user sp2:

```
CALL sp_iqhelp sp2;
```

This example returns information about the event e1:

```
CALL sp_iqhelp e1;
```

This example returns information about the data type dt1:

```
CALL sp_iqhelp dt1;
```

This example returns summary information about all system objects \(owned by dbo or SYS\):

```
CALL sp_iqhelp NULL, NULL, NULL, SYSTEM;
```

This example returns the error message ***owned by user"Object 'non\_existing\_obj' not found"***, as the object non\_existing\_obj does not exist:

```
CALL sp_iqhelp non_existing_obj;
```

**Related Information**  


[sp\_iqcolumn System Procedure for Data Lake Relational Engine](sp-iqcolumn-system-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqconstraint System Procedure for Data Lake Relational Engine](sp-iqconstraint-system-procedure-for-data-lake-relational-engine-a5a0395.md "Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.")

[sp\_iqdatatype System Procedure for Data Lake Relational Engine](sp-iqdatatype-system-procedure-for-data-lake-relational-engine-a5a247c.md "Displays information about system data types and user-defined data types.")

[sp\_iqevent System Procedure for Data Lake Relational Engine](sp-iqevent-system-procedure-for-data-lake-relational-engine-a5a872a.md "Displays information about system and user-defined events.")

[sp\_iqindex and sp\_iqindex\_alt System Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-system-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqpkeys System Procedure for Data Lake Relational Engine](sp-iqpkeys-system-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm System Procedure for Data Lake Relational Engine](sp-iqprocparm-system-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iq\_reset\_identity System Procedure for Data Lake Relational Engine](sp-iq-reset-identity-system-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqtable System Procedure for Data Lake Relational Engine](sp-iqtable-system-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

[sp\_iqview System Procedure for Data Lake Relational Engine](sp-iqview-system-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

