<!-- loio3be994196c5f1014a71dae23a2f5831c -->

# SYSPROCPERM System View for Data Lake Relational Engine

Each row of the SYSPROCPERM system view describes a user who has been granted EXECUTE privilege on a procedure. The underlying system table for this view is ISYSPROCPERM.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




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

**Related Information**  


[SYSPROCPERM System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/69c44e964a2b4f0aa2bcf89a5d1b359a.html "Each row of the SYSPROCPERM system view describes a user who has been granted EXECUTE privilege on a procedure. The underlying system table for this view is ISYSPROCPERM.") :arrow_upper_right:

