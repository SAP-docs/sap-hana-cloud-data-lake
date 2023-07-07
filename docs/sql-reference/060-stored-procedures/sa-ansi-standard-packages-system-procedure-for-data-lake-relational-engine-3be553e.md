<!-- loio3be553e66c5f1014ae7590829b8dfdbf -->

# sa\_ansi\_standard\_packages System Procedure for Data Lake Relational Engine

Returns information about the non-core SQL extensions used in a SQL statement.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_ansi_standard_packages(
<standard>
, <statement>
)
```



<a name="loio3be553e66c5f1014ae7590829b8dfdbf__sa_ansi_standard_packages_param1"/>

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



<a name="loio3be553e66c5f1014ae7590829b8dfdbf__sa_ansi_standard_packages_resultset1"/>

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



<a name="loio3be553e66c5f1014ae7590829b8dfdbf__sa_ansi_standard_packages_remarks1"/>

## Remarks

If there are no non-core extensions used for the statement, the result set is empty.



<a name="loio3be553e66c5f1014ae7590829b8dfdbf__sa_ansi_standard_packages_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on the procedure.



<a name="loio3be553e66c5f1014ae7590829b8dfdbf__sa_ansi_standard_packages_sideeffects1"/>

## Side Effects

None

**Related Information**  


[sa_ansi_standard_packages System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/534a9382c24b4f368bf19a9e82500a72.html "Returns information about the non-core SQL extensions used in a SQL statement.") :arrow_upper_right:

