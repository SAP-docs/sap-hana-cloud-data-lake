<!-- loioe590a4b345ae4767ad000e6cac772827 -->

# PROCEDURE OWNER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the owner of the current procedure, or NULL if queried outside of a procedure context.



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
>         -   For information on using the REMOTE\_EXECUTE\_QUERY procedure, see [Query Using the REMOTE_EXECUTE_QUERY procedure in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/4192f252c2af4136aebadbd1a806b139.html "Use the REMOTE_EXECUTE_QUERY function to query data lake Relational Engine objects without having to reference an SAP HANA database virtual table in the query.") :arrow_upper_right:.



<a name="loioe590a4b345ae4767ad000e6cac772827__section_dnw_42r_btb"/>

## Data Type

STRING



<a name="loioe590a4b345ae4767ad000e6cac772827__section_mxj_p2r_btb"/>

## Remarks

Use PROCEDURE OWNER, INVOKING USER, SESSION USER, and EXECUTING USER to determine which users can execute, and are executing, procedures and user-defined functions. Depending on how many layers of nesting in a particular procedure call, the EXECUTING USER and INVOKING USER can and do change.

PROCEDURE\_OWNER is equivalent to PROCEDURE OWNER.



<a name="loioe590a4b345ae4767ad000e6cac772827__section_dkx_p2r_btb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>

