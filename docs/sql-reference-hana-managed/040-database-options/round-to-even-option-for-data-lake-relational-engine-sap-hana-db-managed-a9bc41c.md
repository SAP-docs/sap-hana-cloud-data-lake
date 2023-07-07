<!-- loioa9bc41c21e7a44b39e48a3bed69742e5 -->

# ROUND\_TO\_EVEN Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls behavior of the SQL function ROUND when querying data lake Relational Engine tables.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loioa9bc41c21e7a44b39e48a3bed69742e5__section_lyv_s3z_lrb"/>

## Syntax

```
ROUND_TO_EVEN = { ON | OFF }
```



<a name="loioa9bc41c21e7a44b39e48a3bed69742e5__section_dhh_t3z_lrb"/>

## Allowed Values

ON, OFF



<a name="loioa9bc41c21e7a44b39e48a3bed69742e5__section_pnt_53z_lrb"/>

## Default

OFF



<a name="loioa9bc41c21e7a44b39e48a3bed69742e5__section_ojw_h5b_dxb"/>

## Privileges

Privilege Category: SYSTEM



### 

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loioa9bc41c21e7a44b39e48a3bed69742e5__section_ubm_v3z_lrb"/>

## Scope

-   Option can be set at the database \(PUBLIC\) level only.

-   Takes effect immediately.




<a name="loioa9bc41c21e7a44b39e48a3bed69742e5__section_tdx_v3z_lrb"/>

## Remarks

The ROUND function rounds the digits after the decimal to the nearest value using the specified number of places. When the value of the last digit of the specified number of places is 5 \(exactly half way between the two nearest values\), the ROUND\_TO\_EVEN option determines how the digit is rounded. When set to ON, the digit rounds to the nearest even number. When set to OFF, the digit rounds to the value with the largest absolute value.



<a name="loioa9bc41c21e7a44b39e48a3bed69742e5__section_ofc_1jz_lrb"/>

## Examples

Table MyTable contains DOUBLE\(10,2\) values:


<table>
<tr>
<th valign="top">

c1



</th>
</tr>
<tr>
<td valign="top">

\-0.35



</td>
</tr>
<tr>
<td valign="top">

\-0.25



</td>
</tr>
<tr>
<td valign="top">

0.25



</td>
</tr>
<tr>
<td valign="top">

0.35



</td>
</tr>
</table>

Execute:

```
select c1, round(c1, 1) from MyTable order by c1;
```

When ROUND\_TO\_EVEN is OFF, the query returns:


<table>
<tr>
<th valign="top">

c1



</th>
<th valign="top">

round\(MyTable,c1,1\)



</th>
</tr>
<tr>
<td valign="top">

\-0.35



</td>
<td valign="top">

\-0.4



</td>
</tr>
<tr>
<td valign="top">

\-0.25



</td>
<td valign="top">

\-0.3



</td>
</tr>
<tr>
<td valign="top">

0.25



</td>
<td valign="top">

0.3



</td>
</tr>
<tr>
<td valign="top">

0.35



</td>
<td valign="top">

0.4



</td>
</tr>
</table>

When ROUND\_TO\_EVEN is ON, the query returns:


<table>
<tr>
<th valign="top">

c1



</th>
<th valign="top">

round\(MyTable,c1,1\)



</th>
</tr>
<tr>
<td valign="top">

\-0.35



</td>
<td valign="top">

\-0.4



</td>
</tr>
<tr>
<td valign="top">

\-0.25



</td>
<td valign="top">

\-0.2



</td>
</tr>
<tr>
<td valign="top">

0.25



</td>
<td valign="top">

0.2



</td>
</tr>
<tr>
<td valign="top">

0.35



</td>
<td valign="top">

0.4



</td>
</tr>
</table>

**Related Information**  


[SQL Statements in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/sql-statements-in-data-lake-relational-engine-sap-hana-db-managed-2d1725b.md "Execute data lake Relational Engine SQL statements.")

[ROUND_TO_EVEN Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a27d00e384f210158811cdeec5401d23.html "Controls behavior of the SQL function ROUND when querying data lake Relational Engine tables.") :arrow_upper_right:

