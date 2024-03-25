<!-- loio69c44e964a2b4f0aa2bcf89a5d1b359a -->

# SYSPROCPERM System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row of the SYSPROCPERM system view describes a user who has been granted EXECUTE privilege on a procedure. The underlying system table for this view is ISYSPROCPERM.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user, and using SAP HANA database REMOTE\_EXECUTE\_QUERY.





<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

proc\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The procedure number uniquely identifies the procedure for which EXECUTE privilege has been granted.

</td>
</tr>
<tr>
<td valign="top">

grantee

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The user number of the privilege grantee.

</td>
</tr>
<tr>
<td valign="top">

executeauth

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates the grantee's permissions on the procedure:

-   Y - Grantee can execute but not re-grant the procedure.
-   G - Grantee can execute and re-grant the procedure.
-   N - Grantee can neither execute nor re-grant the procedure.



</td>
</tr>
</table>



<a name="loio69c44e964a2b4f0aa2bcf89a5d1b359a__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSPROCPERM System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/3be994196c5f1014a71dae23a2f5831c.html "Each row of the SYSPROCPERM system view describes a user who has been granted EXECUTE privilege on a procedure. The underlying system table for this view is ISYSPROCPERM.") :arrow_upper_right:

