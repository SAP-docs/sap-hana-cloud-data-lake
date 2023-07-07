<!-- loioa47a41ccbfb74a0fb5f9ac57be0af957 -->

# INVOKING USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the user that invoked the current procedure, or returns the current logged in user if no procedure is executing.



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



<a name="loioa47a41ccbfb74a0fb5f9ac57be0af957__section_zxt_ydr_btb"/>

## Data Type

STRING



<a name="loioa47a41ccbfb74a0fb5f9ac57be0af957__section_ldm_zdr_btb"/>

## Remarks

Use INVOKING USER, SESSION USER, EXECUTING USER, and PROCEDURE OWNER to determine which users can execute, and are executing, procedures. Depending on how many layers of nesting in a particular procedure call, the INVOKING USER and EXECUTING USER can and do change.

INVOKING\_USER is equivalent to INVOKING USER.



<a name="loioa47a41ccbfb74a0fb5f9ac57be0af957__section_rgx_zdr_btb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>

