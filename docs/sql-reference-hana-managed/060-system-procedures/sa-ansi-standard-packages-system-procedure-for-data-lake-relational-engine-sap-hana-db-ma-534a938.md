<!-- loio534a9382c24b4f368bf19a9e82500a72 -->

# sa\_ansi\_standard\_packages System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns information about the non-core SQL extensions used in a SQL statement.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Running Procedures](remote-execute-usage-examples-for-running-procedures-3e7f86d.md) for more information.



```
sa_ansi_standard_packages(
<standard>
, <statement>
)
```



<a name="loio534a9382c24b4f368bf19a9e82500a72__section_jsn_zr4_rrb"/>

## Parameters


<dl>
<dt><b>

 *<standard\>* 

</b></dt>
<dd>

Use this LONG VARCHAR parameter to specify the standard to use for the core extensions. One of SQL:1999 or SQL:2003.



</dd><dt><b>

 *<statement\>* 

</b></dt>
<dd>

Use this LONG VARCHAR parameter to specify the SQL statement to evaluate.



</dd>
</dl>



<a name="loio534a9382c24b4f368bf19a9e82500a72__section_ntb_1s4_rrb"/>

## Result Set


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

package\_id



</td>
<td valign="top">

VARCHAR\(10\)



</td>
<td valign="top">

The feature identifier.



</td>
</tr>
<tr>
<td valign="top">

package\_name



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The feature name.



</td>
</tr>
</table>



<a name="loio534a9382c24b4f368bf19a9e82500a72__section_vln_1s4_rrb"/>

## Remarks

If there are no non-core extensions used for the statement, the result set is empty.



<a name="loio534a9382c24b4f368bf19a9e82500a72__section_u51_bkf_3jb"/>

## Permissions

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



## Side Effects

None

**Related Information**  


[sa_ansi_standard_packages System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/3be553e66c5f1014ae7590829b8dfdbf.html "Returns information about the non-core SQL extensions used in a SQL statement.") :arrow_upper_right:

