<!-- loio550b14e294624916ad59f4815d8ac248 -->

# REMOTE\_EXECUTE\_QUERY Procedure

Execute SELECT queries on data lake Relational Engine objects without using an SAP HANA database virtual table in the query.



<a name="loio550b14e294624916ad59f4815d8ac248__sql_function_add_workdays_1sql_function_add_workdays_syntax"/>

## Syntax

```
SELECT <hana_select_criteria> FROM REMOTE_EXECUTE_QUERY ('[/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_[/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <relational_container_name> (varname] (span]_SOURCE', 'SELECT <data_lake_select_criteria>');
```



<a name="loio550b14e294624916ad59f4815d8ac248__sql_function_add_workdays_1sql_function_add_workdays_description"/>

## Description

The REMOTE\_EXECUTE\_QUERY only supports the SELECT statement construct. The SELECT can only include data lake Relational Engine tables, but does support joins.



<a name="loio550b14e294624916ad59f4815d8ac248__section_knm_1s2_q5b"/>

## Permissions

Requires the SAP HANA database REMOTE EXECUTE system privilege on the relational container remote source \(SYSHDL\_*<relational\_container\_name\>*\_SOURCE.



<a name="loio550b14e294624916ad59f4815d8ac248__sql_function_add_workdays_1sql_function_add_workdays_examples"/>

## Examples

The following example performs a query on the data lake Relational Engine table MyTable, using the remote source SYSHDL\_CONTAINER1\_SOURCE:

```
SELECT * FROM REMOTE_EXECUTE_QUERY ('[/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1_SOURCE', 'SELECT * FROM MYTABLE');
```

The following example returns the result set of the system procedure sp\_displayroles:

```
SELECT * FROM REMOTE_EXECUTE_QUERY ('[/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1_SOURCE', 'SELECT * FROM sp_displayroles()');
```

The following example performs a query with a join.

```
SELECT * FROM REMOTE_EXECUTE_QUERY ('[/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1_SOURCE', '
   SELECT D.DEPT_NAME, E.EMP_NAME 
   FROM DEPARTMENT AS D 
   JOIN EMPLOYEES AS E ON ( D.DEPT_ID = E.DEPT_ID )');
```

**Related Information**  


[Query Using the REMOTE_EXECUTE_QUERY Procedure in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/4192f252c2af4136aebadbd1a806b139.html "Use the REMOTE_EXECUTE_QUERY procedure to execute SELECT queries on data lake Relational Engine objects without using an SAP HANA database virtual table in the query.") :arrow_upper_right:

[Granting Permissions to Run REMOTE_EXECUTE_QUERY in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/1924577fe8494d75894947de47badaa9.html "You need permissions to the relational container source before you can use the REMOTE_EXECUTE_QUERY procedure.") :arrow_upper_right:

