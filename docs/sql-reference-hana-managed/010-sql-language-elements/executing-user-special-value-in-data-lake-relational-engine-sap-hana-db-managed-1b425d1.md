<!-- loio1b425d11a3764ef2924f23e02f2f597f -->

# EXECUTING USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

SQL special value that returns the current effective user.



<a name="loio1b425d11a3764ef2924f23e02f2f597f__section_agt_pxr_btb"/>

## Usage

Data lake Relational Engine \(SAP HANA DB-Managed\) special values can be used when connected as follows:

-   To use a special value as a column default when creating a table, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure

-   To return an expression as part of a SELECT statement that returns a value, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXEUCTE\_QUERY function.




<a name="loio1b425d11a3764ef2924f23e02f2f597f__section_uj3_spr_btb"/>

## Data Type

STRING



<a name="loio1b425d11a3764ef2924f23e02f2f597f__section_hjt_spr_btb"/>

## Remarks

Use EXECUTING USER, INVOKING USER, SESSION USER, and PROCEDURE OWNER to determine which users can execute, and are executing, procedures and user-defined functions. Depending on how many layers of nesting in a particular procedure call, and based on whether the previous and current procedure are SQL SECURITY DEFINER or SQL SECURITY INVOKER, the EXECUTING USER, and INVOKING USER can and do change.

EXECUTING\_USER is equivalent to EXECUTING USER.



<a name="loio1b425d11a3764ef2924f23e02f2f597f__section_yqj_tpr_btb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>

