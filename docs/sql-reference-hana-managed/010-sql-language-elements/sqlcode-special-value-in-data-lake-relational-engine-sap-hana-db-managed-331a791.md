<!-- loio331a79135cce4f3694f4fbe7ed33eaea -->

# SQLCODE Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the current SQLCODE value.



> ### Restriction:  
> Data lake Relational Engine \(SAP HANA DB-Managed\) special values can be used when connected as follows:
> 
> -   To use a special value as a column default when creating a table, you must be:
>     -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>         -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](../030-sql-statements/remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).
> 
> 
> -   To return an expression as part of a SELECT statement that returns a value, you must be:
>     -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXEUCTE\_QUERY function.
>         -   For information on using the REMOTE\_EXECUTE\_QUERY procedure, see [Query Using the REMOTE_EXECUTE_QUERY procedure in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/4192f252c2af4136aebadbd1a806b139.html "Use the REMOTE_EXECUTE_QUERY procedure to execute SELECT queries on data lake Relational Engine objects without using an SAP HANA database virtual table in the query.") :arrow_upper_right:.



<a name="loio331a79135cce4f3694f4fbe7ed33eaea__section_fsz_x2r_btb"/>

## Data Type

STRING



<a name="loio331a79135cce4f3694f4fbe7ed33eaea__section_cb4_y2r_btb"/>

## Remarks

The SQLCODE value is set after each statement. You can check the SQLCODE to see whether or not the statement succeeded.



<a name="loio331a79135cce4f3694f4fbe7ed33eaea__section_kpw_y2r_btb"/>

## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 