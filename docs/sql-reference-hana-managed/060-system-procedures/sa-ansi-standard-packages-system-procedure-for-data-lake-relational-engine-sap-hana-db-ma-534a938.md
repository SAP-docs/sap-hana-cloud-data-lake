<!-- loio534a9382c24b4f368bf19a9e82500a72 -->

# sa\_ansi\_standard\_packages System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns information about the non-core SQL extensions used in a SQL statement.



<a name="loio534a9382c24b4f368bf19a9e82500a72__section_ag2_hhd_pzb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

> ### Restriction:  
> This syntax cannot be run when connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_QUERY.



```
sa_ansi_standard_packages(
   <standard>, <statement> )
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

Objects referenced in the *<statement\>* parameter must reside in a user-created schema in a relational container. They cannot reside in the default schema \(SYSHDL\_*<relational\_container\_name\>*\).

For example, the following call fails because table Z1 is in the default relational container syshdl\_container1:

```
CALL sa_ansi_standard_packages( 'SQL:2003', 'SELECT * FROM syshdl_container1.Z1');
```

However, the following call succeeds because table Y1 is in the user-create schema syshdl\_container1\_myschema1:

```
CALL sa_ansi_standard_packages( 'SQL:2003', 'SELECT * FROM syshdl_container1_myschema1.Y1');
```



<a name="loio534a9382c24b4f368bf19a9e82500a72__section_plr_s1b_1yb"/>

## Privileges



### 

Requires EXECUTE object-level privilege on this procedure.



## Side Effects

None

**Related Information**  


[sa_ansi_standard_packages System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/3be553e66c5f1014ae7590829b8dfdbf.html "Returns information about the non-core SQL extensions used in a SQL statement.") :arrow_upper_right:

