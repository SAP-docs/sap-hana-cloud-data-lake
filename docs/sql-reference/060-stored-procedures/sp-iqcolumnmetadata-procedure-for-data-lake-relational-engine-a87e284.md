<!-- loioa87e284f84f21015b893da0ff4572d65 -->

# sp\_iqcolumnmetadata Procedure for Data Lake Relational Engine

Returns details about column indexes in one or more tables.



<a name="loioa87e284f84f21015b893da0ff4572d65__section_vt2_cwh_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqcolumnmetadata [ <table.name> [, <owner-name> ] ];
```



<a name="loioa87e284f84f21015b893da0ff4572d65__section_wtj_yl4_tvb"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

uname

</td>
<td valign="top">

Owner of the table.

</td>
</tr>
<tr>
<td valign="top">

tname

</td>
<td valign="top">

Name of the table.

</td>
</tr>
<tr>
<td valign="top">

iname

</td>
<td valign="top">

Name of the index.

</td>
</tr>
<tr>
<td valign="top">

col

</td>
<td valign="top">

Column number.

</td>
</tr>
<tr>
<td valign="top">

cname

</td>
<td valign="top">

Column name.

</td>
</tr>
<tr>
<td valign="top">

domain\_name

</td>
<td valign="top">

Column data type.

</td>
</tr>
<tr>
<td valign="top">

width

</td>
<td valign="top">

Column width in bytes.

</td>
</tr>
<tr>
<td valign="top">

NBit

</td>
<td valign="top">

Bit count \(NBit level 1-31\).

</td>
</tr>
<tr>
<td valign="top">

TokenCount

</td>
<td valign="top">

Approximate number of distinct values.

</td>
</tr>
<tr>
<td valign="top">

DictSize

</td>
<td valign="top">

Dictionary Value size.

</td>
</tr>
<tr>
<td valign="top">

CountSize

</td>
<td valign="top">

Dictionary Count size.

</td>
</tr>
<tr>
<td valign="top">

"IQ Unique"

</td>
<td valign="top">

IQ UNIQUE value from CREATE/ALTER TABLE.

</td>
</tr>
<tr>
<td valign="top">

Style

</td>
<td valign="top">

FP index type.

</td>
</tr>
</table>



## Parameters


<dl>
<dt><b>

*<table.name\>*

</b></dt>
<dd>

A parameter that specifies the name of the table.



</dd><dt><b>

*<owner-name\>*

</b></dt>
<dd>

A parameter that specifies the owner name.



</dd>
</dl>



<a name="loioa87e284f84f21015b893da0ff4572d65__section_rqy_bvz_mbb"/>

## Remarks

sp\_iqcolumnmetadata reads the index metadata to return details about column indexes in both base and global temporary tables. Index metadata reported for a global temporary table is for the individual instance of that table.

Include the optional *<table.name\>* parameter to generate details for that table. Omit the *<table.name\>* parameter to generate details for all tables in the database.



## Privileges

Requires EXECUTE object-level privilege on the procedure. If you own the object referenced by the procedure, no additional privilege is required.

For objects owned by others, you need one of the following privileges:

-   ALTER ANY INDEX system privilege
-   ALTER ANY OBJECT system privilege
-   REFERENCES object-level privilege on the table



## Side Effects

None

**Related Information**  


[sp\_iqindexmetadata Procedure for Data Lake Relational Engine](sp-iqindexmetadata-procedure-for-data-lake-relational-engine-a5ad0e4.md "Displays index metadata for a given index.")

