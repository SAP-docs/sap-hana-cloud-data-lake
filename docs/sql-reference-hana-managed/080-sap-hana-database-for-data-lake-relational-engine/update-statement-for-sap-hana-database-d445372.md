<!-- loiod445372322a34e01b1cb96a5a467e8aa -->

# UPDATE Statement for SAP HANA Database

Changes the values of the records of a table.



<a name="loiod445372322a34e01b1cb96a5a467e8aa__sql_update_1sql_update_syntax"/>

## Syntax

```
UPDATE [ <top_clause> ] [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <hana_relational_container_schema_name> (varname].[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <virtual_table_name> (varname]
   <set_clause>
   [ WHERE <condition> ]
   [ <hint_clause> ]
```



<a name="loiod445372322a34e01b1cb96a5a467e8aa__sql_update_1sql_update_syntax_elements"/>

## Syntax Elements

 *<top\_clause\>*
 :   Limits the number of updated records \(for example, for chunkwise updates\).

    ```
    <top_clause> ::= TOP <unsigned_integer>
    ```

    *<unsigned\_integer\>* defines the number of records updated in one chunk. This parameter is not supported for variants of UPDATE statements like UPDATE MERGE DELTA, UPDATE PRELOAD, UPDATE UNLOAD, and UPDATE MOVE.

  *<hana\_relational\_container\_schema\_name\>*
 :   Specifies the SAP HANA database schema of the virtual table.

  *<virtual\_table\_name\>*
 :   Specifies the virtual table where the UPDATE is performed.

  *<set\_clause\>*
 :   Specifies the column names and associated values to be set by the update statement.

    ```
    <set_clause> ::= 
     SET {<column_name> = <expression> 
     | ( <with_clause> <subquery> ) },...
    ```

    For the definitions of the *<with\_clause\>* and *<subquery\>*, see the SELECT statement. The *<with\_clause\>* can be used with column names, not with column lists.

  WHERE *<condition\>*
 :   Specifies the conditions when the command should be performed.

    ```
    <condition> ::= 
     <condition> OR <condition>
     | <condition> AND <condition>
     | NOT <condition>
     | ( <condition> )
     | <predicate>
     | CURRENT OF <cursor>
    ```

    WHERE CURRENT OF *<cursor\>* specifies to perform the update at the current position in the cursor.

  *<hint\_clause\>*
 :   For information on hints, see the HINT clause in the SELECT statement.

 

<a name="loiod445372322a34e01b1cb96a5a467e8aa__sql_update_1sql_update_description"/>

## Description

If the WHERE condition is used and is true for a specific row, then an update is performed on that row. If the WHERE clause is omitted, then the UPDATE command updates all records of a table.



<a name="loiod445372322a34e01b1cb96a5a467e8aa__sql_update_1sql_update_examples"/>

## Examples

Create virtual table T1 in schema SYSHDL\_CONTAINER1, and insert two rows into it.

```
CREATE VIRTUAL TABLE [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.V_T1 AT "[/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1_SOURCE"."<NULL>"."[/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1"."T1";
 INSERT INTO [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.V_T1 VALUES (1, 1);
 INSERT INTO [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.V_T1 VALUES (2, 2);
```

Update the rows of table T if the condition in the WHERE clause is true.

```
UPDATE [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.V_T1 SET VAL = VAL + 1 WHERE KEY = 1;
SELECT * FROM [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.V_T1;
```


<table>
<tr>
<td valign="top">

KEY



</td>
<td valign="top">

VAL



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

2



</td>
</tr>
</table>

This example shows how to update all rows of the table by omitting the WHERE clause.

```
UPDATE [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.V_T1 SET VAL = KEY + 10;
SELECT * FROM [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.V_T1;
```


<table>
<tr>
<td valign="top">

KEY



</td>
<td valign="top">

VAL



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

11



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

12



</td>
</tr>
</table>

**Related Information**  


[SELECT Statement for SAP HANA Database](select-statement-for-sap-hana-database-68b8472.md "Queries data from the SAP HANA database.")

