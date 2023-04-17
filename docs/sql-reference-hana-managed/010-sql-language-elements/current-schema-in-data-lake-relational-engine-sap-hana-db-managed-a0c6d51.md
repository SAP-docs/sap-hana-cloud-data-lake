<!-- loioa0c6d51d417d4127b540af0ba1fbd2ba -->

# CURRENT SCHEMA in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a string that contains the name of the current schema for the connection.



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



<a name="loioa0c6d51d417d4127b540af0ba1fbd2ba__section_fvj_dhr_btb"/>

## Data Type

VARCHAR



<a name="loioa0c6d51d417d4127b540af0ba1fbd2ba__section_ydv_dhr_btb"/>

## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 