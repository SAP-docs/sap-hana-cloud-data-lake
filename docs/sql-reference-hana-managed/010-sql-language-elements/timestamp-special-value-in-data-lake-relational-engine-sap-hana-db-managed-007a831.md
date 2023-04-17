<!-- loio007a83140e6549dbac433c392ade1d3c -->

# TIMESTAMP Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns when each row in the table was last modified.



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



<a name="loio007a83140e6549dbac433c392ade1d3c__section_zfj_5fr_btb"/>

## Data Type

TIMESTAMP



<a name="loio007a83140e6549dbac433c392ade1d3c__section_w2v_5fr_btb"/>

## Remarks

When a column is declared with DEFAULT TIMESTAMP, a default value is provided for insert and load operations. The value is updated with the current date and time whenever the row is updated.

On INSERT and LOAD, DEFAULT TIMESTAMP has the same effect as CURRENT TIMESTAMP. On UPDATE, if a column with a default value of TIMESTAMP isn’t explicitly modified, the value of the column is changed to the current date and time.

> ### Note:  
> Data lake Relational Engine doesn’t support DEFAULT values of UTC TIMESTAMP or CURRENT UTC TIMESTAMP. Data lake Relational Engine generates an error every time an attempt is made to insert or update the DEFAULT value of a column of type UTC TIMESTAMP or CURRENT UTC TIMESTAMP.



<a name="loio007a83140e6549dbac433c392ade1d3c__section_vfq_vfr_btb"/>

## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 