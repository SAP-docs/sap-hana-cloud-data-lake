<!-- loioaa33ab91a70f4e2fb315df5b5bed9391 -->

# SESSION USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

SQL special value that stores the user that is currently logged in.



<a name="loioaa33ab91a70f4e2fb315df5b5bed9391__section_agt_pxr_btb"/>

## Usage

Data lake Relational Engine \(SAP HANA DB-Managed\) special values can be used when connected as follows:

-   To use a special value as a column default when creating a table, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user.

-   To return an expression as part of a SELECT statement that returns a value, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user.




<a name="loioaa33ab91a70f4e2fb315df5b5bed9391__section_vmd_1qr_btb"/>

## Data Type

STRING



<a name="loioaa33ab91a70f4e2fb315df5b5bed9391__section_n25_1qr_btb"/>

## Remarks

Use SESSION USER, INVOKING USER, EXECUTING USER, and PROCEDURE OWNER to determine which users can execute, and are executing, procedures and user-defined functions. Depending on how many layers of nesting in a particular procedure call, and based on whether the previous and current procedure are SQL SECURITY DEFINER or SQL SECURITY INVOKER, the INVOKING USER, and EXECUTING USER can and do change. However, SESSION USER always remains the logged in user.

SESSION\_USER is equivalent to SESSION USER.



<a name="loioaa33ab91a70f4e2fb315df5b5bed9391__section_zkk_bqr_btb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>

