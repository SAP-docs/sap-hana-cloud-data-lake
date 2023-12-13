<!-- loio9cf18d5676a747b6b7b5e46070cf3ecc -->

# REMOTE\_EXECUTE\_DDL Procedure for SAP HANA Database

Execute SQL commands on the data lake Relational Engine coordinator.



```
CALL <relational_container_name>.REMOTE_EXECUTE_DDL(
   '<statement_string>' ); 
```



<a name="loio9cf18d5676a747b6b7b5e46070cf3ecc__section_dj3_45x_cjb"/>

## Parameters


<dl>
<dt><b>

*<statement\_string\>*

</b></dt>
<dd>

Specifies the SQL statement to be executed on *<relational\_container\_name\>*.



</dd>
</dl>



<a name="loio9cf18d5676a747b6b7b5e46070cf3ecc__section_zhc_rnx_cjb"/>

## Description

Escape the entire data lake Relational Engine DML or DDL *<statement\_string\>* in single quotation marks \(`'`\).

Escape all strings **inside** the data lake Relational Engine DML or DDL *<statement\_string\>* with two quotation marks \( `''` \).



<a name="loio9cf18d5676a747b6b7b5e46070cf3ecc__section_xlt_rnx_cjb"/>

## Privileges

To use REMOTE\_EXECUTE\_DDL requires one of the following:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE\_DDL procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

> ### Note:  
> REMOTE\_EXECUTE\_DDL connects directly to the data lake Relational Engine coordinator node \(not the writer node\) to process the embedded syntax.



<a name="loio9cf18d5676a747b6b7b5e46070cf3ecc__section_f5l_5nx_cjb"/>

## Example

The following example creates table T1 in data lake Relational Engine.

```
CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE_DDL( 'CREATE TABLE T1 (a INT, b INT)' );
```

