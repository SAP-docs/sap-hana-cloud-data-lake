<!-- loio228acf2626c64212b3589f4d810bdd88 -->

# DELETE Statement for SAP HANA Database

Deletes records from a table where a specified condition is met.



<a name="loio228acf2626c64212b3589f4d810bdd88__sql_delete_1sql_delete_syntax"/>

## Syntax

```
DELETE FROM [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <hana_relational_container_schema_name> (varname].[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <virtual_table_name> (varname] 
   [ WHERE <condition> ] [ <hint_clause> ]
```



<a name="loio228acf2626c64212b3589f4d810bdd88__sql_delete_1sql_delete_syntax_elements"/>

## Syntax Elements

 *<hana\_relational\_container\_schema\_name\>*
 :   Specifies the schema of the virtual table where the deletion is to occur.

  *<virtual\_table\_name\>*
 :   Specifies the virtual table name where the deletion is to occur.

  WHERE *<condition\>*
 :   Specifies the conditions where the command should be performed.

    ```
    <condition> ::= 
     <condition> OR <condition>
     | <condition> AND <condition>
     | NOT <condition>
     | ( <condition> )
     | <predicate>
     | CURRENT OF <cursor>
    ```

    WHERE CURRENT OF *<cursor\>* specifies to perform the delete at the current position in the cursor.

  *<hint\_clause\>*
 :   Specifies the hint clause. For information on specifying hints, see the HINT clause of the SELECT statement.

 

<a name="loio228acf2626c64212b3589f4d810bdd88__sql_delete_1sql_delete_description"/>

## Description

If the WHERE clause is omitted, then DELETE removes all records from a table.



<a name="loio228acf2626c64212b3589f4d810bdd88__sql_delete_1sql_delete_examples"/>

## Examples

This example creates table T1, inserts data into the table, and then deletes values equal to 1 from the table.

Create virtual table T1 and insert some data.

```
CREATE VIRTUAL TABLE [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.V_T1 (KEY INT PRIMARY KEY, VAL INT);
INSERT INTO [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.V_T1 VALUES (1, 1);
INSERT INTO [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.V_T1 VALUES (2, 2);
INSERT INTO [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.V_T1 VALUES (3, 3);
```

Delete from table V\_T1 where the KEY column is equal to 1;

```
DELETE FROM [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.V_T1 WHERE KEY = 1;
```

After executing the previous query, the contents of table V\_T1 are as follows, showing that the first row was deleted from the table:


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

2



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

3



</td>
</tr>
</table>

**Related Information**  


[SELECT Statement for SAP HANA Database](select-statement-for-sap-hana-database-68b8472.md "Queries data from the SAP HANA database.")

