<!-- loio9bc729e3864c471ea372794526b16329 -->

# Finding 6 Digits of Precision TIMESTAMP Columns in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Identify all data lake Relational Engine tables containing TIMESTAMP data type columns using 6 digits of precision.



<a name="loio9bc729e3864c471ea372794526b16329__section_h5g_b1l_31c"/>

## Prerequisites

This data lake Relational Engine task can be completed when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user.

Requires:

-   You have the REMOTE EXECUTE privilege on the remote source *<hana\_relational\_container\_schema\>*\_SOURCE.



<a name="loio9bc729e3864c471ea372794526b16329__section_wbb_c1l_31c"/>

## Context

To identify existing tables with TIMESTAMP columns using 6 digits of precision, execute:

```
SELECT * FROM REMOTE_EXECUTE_QUERY ('SYSHDL_<relational_container_name>_SOURCE', 
   'SELECT t.table_name, c.column_name, u.user_name
      FROM SYSTABCOL c, SYSTAB t, SYSUSER u
      WHERE t.table_id = c.table_id 
         AND u.user_id = t.creator
         AND c.domain_id = 13
         AND t.creator not in (0, 1, 3, 6)');
```

The result set returns the table owner or schema, table name, and column name for any table containing a TIMESTAMP column using 6 digits of precision. In this example, three TIMESTAMP columns within tables T1 and T2 are found.


<table>
<tr>
<th valign="top">

table\_name

</th>
<th valign="top">

column\_name

</th>
<th valign="top">

user\_name

</th>
</tr>
<tr>
<td valign="top">

T1

</td>
<td valign="top">

a

</td>
<td valign="top">

SYSHDL\_CONTAINER1\_MYSCHEMA1

</td>
</tr>
<tr>
<td valign="top">

T1

</td>
<td valign="top">

c

</td>
<td valign="top">

SYSHDL\_CONTAINER1\_MYSCHEMA1

</td>
</tr>
<tr>
<td valign="top">

T2

</td>
<td valign="top">

b

</td>
<td valign="top">

SYSHDL\_CONTAINER1

</td>
</tr>
</table>



<a name="loio9bc729e3864c471ea372794526b16329__section_tlt_2rh_41c"/>

## What's Next

Once columns are identified, you need to determine if the columns have any keys, constraints, or indexes assigned. These must be identified **before** migrating the column as they will be lost once migration is complete. See [Identifying Column Keys, Constraints, and Indexes on TIMESTAMP Data Type Columns in Data Lake Relational Engine \(SAP HANA DB-Managed\)](identifying-column-keys-constraints-and-indexes-on-timestamp-data-type-columns-in-data-la-c0c6b41.md).

