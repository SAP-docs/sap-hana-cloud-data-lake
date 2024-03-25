<!-- loioa9bc41c21e7a44b39e48a3bed69742e5 -->

# ROUND\_TO\_EVEN Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls behavior of the SQL function ROUND when querying data lake Relational Engine tables.



<a name="loioa9bc41c21e7a44b39e48a3bed69742e5__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user..
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



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

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method and whether you are setting the option temporarily or permanently:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user:

</b></dt>
<dd>

-   To set a database option permanently, use REMOTE\_EXECUTE.

    Requires one of:

    -   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
    -   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

    -   See [REMOTE\_EXECUTE Guidance and Examples for Setting Permanent Database Options](remote-execute-guidance-and-examples-for-setting-permanent-database-options-0023bea.md).


-   To set a database option temporarily, use the SET\_TEMPORARY\_OPTION procedure, which requires you be a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.

    -   See [SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md).





</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

-   Requires the SET ANY CUSTOMER SYSTEM OPTION system privilege to set this database option.



</dd>
</dl>



<a name="loioa9bc41c21e7a44b39e48a3bed69742e5__section_ubm_v3z_lrb"/>

## Scope


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

PUBLIC Role

</th>
<th valign="top">

For Current User

</th>
<th valign="top">

For Other Users

</th>
</tr>
<tr>
<td valign="top">

Allowed to set permanently?

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
</table>



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


[SQL Statements in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/sql-statements-in-data-lake-relational-engine-sap-hana-db-managed-2d1725b.md "Data lake Relational Engine supports many SQL statements to allow you to perform such tasks as create database objects, administer your system, and manipulate data.")

[ROUND_TO_EVEN Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a27d00e384f210158811cdeec5401d23.html "Controls behavior of the SQL function ROUND when querying data lake Relational Engine tables.") :arrow_upper_right:

