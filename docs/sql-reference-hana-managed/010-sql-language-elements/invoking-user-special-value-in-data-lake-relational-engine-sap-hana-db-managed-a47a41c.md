<!-- loioa47a41ccbfb74a0fb5f9ac57be0af957 -->

# INVOKING USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the user that invoked the current procedure, or returns the current logged in user if no procedure is executing.



<a name="loioa47a41ccbfb74a0fb5f9ac57be0af957__section_agt_pxr_btb"/>

## Usage

Data lake Relational Engine \(SAP HANA DB-Managed\) special values can be used when connected as follows:

-   To use a special value as a column default when creating a table, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure

-   To return an expression as part of a SELECT statement that returns a value, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXEUCTE\_QUERY function.




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

