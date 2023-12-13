<!-- loio331a79135cce4f3694f4fbe7ed33eaea -->

# SQLCODE Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the current SQLCODE value.



<a name="loio331a79135cce4f3694f4fbe7ed33eaea__section_agt_pxr_btb"/>

## Usage

Data lake Relational Engine \(SAP HANA DB-Managed\) special values can be used when connected as follows:

-   To use a special value as a column default when creating a table, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure

-   To return an expression as part of a SELECT statement that returns a value, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXEUCTE\_QUERY function.




<a name="loio331a79135cce4f3694f4fbe7ed33eaea__section_fsz_x2r_btb"/>

## Data Type

STRING



<a name="loio331a79135cce4f3694f4fbe7ed33eaea__section_cb4_y2r_btb"/>

## Remarks

The SQLCODE value is set after each statement. You can check the SQLCODE to see whether or not the statement succeeded.



<a name="loio331a79135cce4f3694f4fbe7ed33eaea__section_kpw_y2r_btb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>

