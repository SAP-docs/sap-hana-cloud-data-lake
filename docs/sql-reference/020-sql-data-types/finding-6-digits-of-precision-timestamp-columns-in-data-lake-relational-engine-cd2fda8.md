<!-- loiocd2fda8d5cf74dc3a2bd3cea5f72202b -->

# Finding 6 Digits of Precision TIMESTAMP Columns in Data Lake Relational Engine

Identify all data lake Relational Engine tables containing TIMESTAMP data type columns using 6 digits of precision.



<a name="loiocd2fda8d5cf74dc3a2bd3cea5f72202b__find_6_digits_section1"/>

## Prerequisites

This data lake Relational Engine task can be completed when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

Requires:

-   You have the SELECT ANY TABLE system privilege.



<a name="loiocd2fda8d5cf74dc3a2bd3cea5f72202b__find_6_digits_section2"/>

## Context

To identify existing tables with TIMESTAMP columns using 6 digits of precision, execute:

```
SELECT t.table_name, c.column_name, u.user_name
   FROM SYSTABCOL c, SYSTAB t, SYSUSER u
   WHERE t.table_id = c.table_id 
      AND u.user_id = t.creator
      AND c.domain_id = 13
      AND t.creator not in (0, 1, 3, 6);
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

HDLADMIN

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

HDLADMIN

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

MYSCHEMA1

</td>
</tr>
</table>



<a name="loiocd2fda8d5cf74dc3a2bd3cea5f72202b__find_6_digits_whats_next"/>

## What's Next

Once columns are identified, you need to determine if the columns have any keys, constraints,comments, grants, or indexes assigned. These must be identified **before** migrating the column as they will be lost once migration is complete. See [Identifying Column Keys, Constraints, Comments, Grants, and Indexes on TIMESTAMP Data Type Columns in Data Lake Relational Engine](identifying-column-keys-constraints-comments-grants-and-indexes-on-timestamp-data-type-co-bb68adb.md).

