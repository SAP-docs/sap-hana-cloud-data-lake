<!-- loio1b425d11a3764ef2924f23e02f2f597f -->

# EXECUTING USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

SQL special value that returns the current effective user.



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



<a name="loio1b425d11a3764ef2924f23e02f2f597f__section_uj3_spr_btb"/>

## Data Type

STRING



<a name="loio1b425d11a3764ef2924f23e02f2f597f__section_hjt_spr_btb"/>

## Remarks

Use EXECUTING USER, INVOKING USER, SESSION USER, and PROCEDURE OWNER to determine which users can execute, and are executing, procedures and user-defined functions. Depending on how many layers of nesting in a particular procedure call, and based on whether the previous and current procedure are SQL SECURITY DEFINER or SQL SECURITY INVOKER, the EXECUTING USER, and INVOKING USER can and do change.

EXECUTING\_USER is equivalent to EXECUTING USER.



<a name="loio1b425d11a3764ef2924f23e02f2f597f__section_yqj_tpr_btb"/>

## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 