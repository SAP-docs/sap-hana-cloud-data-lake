<!-- loioebe6a39a82a3421b8bb3a2100eda6a79 -->

# REMOTE\_EXECUTE Procedure for SAP HANA Database

Execute SQL commands on the remote data lake Relational Engine source.



```
CALL [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <relational_container_name> (varname].REMOTE_EXECUTE(
   '<statement_string>' ); 
```



<a name="loioebe6a39a82a3421b8bb3a2100eda6a79__section_dj3_45x_cjb"/>

## Parameters

 *<statement\_string\>*
 :   Specifies the SQL statement to be executed on *<relational\_container\_name\>*.

 

<a name="loioebe6a39a82a3421b8bb3a2100eda6a79__section_zhc_rnx_cjb"/>

## Description

Escape the entire data lake Relational Engine DML or DDL *<statement\_string\>* in single quotation marks \(`'`\).

Escape all strings **inside** the data lake Relational Engine DML or DDL *<statement\_string\>* with two quotation marks \( `''` \).



<a name="loioebe6a39a82a3421b8bb3a2100eda6a79__section_xlt_rnx_cjb"/>

## Privileges

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loioebe6a39a82a3421b8bb3a2100eda6a79__section_f5l_5nx_cjb"/>

## Example

The following example creates table T1 in data lake Relational Engine.

```
CALL [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.REMOTE_EXECUTE( 'CREATE TABLE T1 (a INT, b INT)' );
```
