<!-- loio336e6f16ef0b4dbeac5a0f16a1e8b15f -->

# CURRENT USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a string that contains the user ID of the current connection.



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



<a name="loio336e6f16ef0b4dbeac5a0f16a1e8b15f__section_xlx_ndr_btb"/>

## Data Type

STRING

CURRENT USER can be used as a default value in columns with character data types.



<a name="loio336e6f16ef0b4dbeac5a0f16a1e8b15f__section_kfx_4dr_btb"/>

## Remarks

CURRENT USER can be used as a default value in columns with character data types.

On UPDATE, columns with a default value of CURRENT USER are not changed.



<a name="loio336e6f16ef0b4dbeac5a0f16a1e8b15f__section_ulg_pdr_btb"/>

## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 **Related Information**  


[CURRENT TIMESTAMP Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)](current-timestamp-special-value-in-data-lake-relational-engine-sap-hana-db-managed-4bbfdd6.md "Combines CURRENT DATE and CURRENT TIME to form a TIMESTAMP value containing the year, month, day, hour, minute, second, and fraction of a second.")

[USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)](user-special-value-in-data-lake-relational-engine-sap-hana-db-managed-8eda34d.md "Returns a string that contains the user ID of the current connection.")
