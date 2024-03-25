<!-- loioa5fbd83484f210158d6fe1b9b7331051 -->

# sa\_text\_index\_stats System Procedure for Data Lake Relational Engine

Returns statistical information about the TEXT indexes in the database.



<a name="loioa5fbd83484f210158d6fe1b9b7331051__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_text_index_stats( )
```



<a name="loioa5fbd83484f210158d6fe1b9b7331051__section_zxk_2mm_zyb"/>

## Parameters

None



<a name="loioa5fbd83484f210158d6fe1b9b7331051__iq_iquda_94"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`owner_id`

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

ID of the owner of the table

</td>
</tr>
<tr>
<td valign="top">

`table_id`

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

ID of the table

</td>
</tr>
<tr>
<td valign="top">

`index_id`

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

ID of the TEXT index

</td>
</tr>
<tr>
<td valign="top">

`text_config_id`

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

ID of the text configuration referenced by the TEXT index

</td>
</tr>
<tr>
<td valign="top">

`owner_name`

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Name of the owner

</td>
</tr>
<tr>
<td valign="top">

`table_name`

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Name of the table

</td>
</tr>
<tr>
<td valign="top">

`index_name`

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Name of the TEXT index

</td>
</tr>
<tr>
<td valign="top">

`text_config_name`

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Name of the text configuration object

</td>
</tr>
<tr>
<td valign="top">

`doc_count`

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Total number of indexed column values in the TEXT index

</td>
</tr>
<tr>
<td valign="top">

`doc_length`

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Total length of data in the TEXT index

</td>
</tr>
<tr>
<td valign="top">

`pending_length`

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Total length of the pending changes

</td>
</tr>
<tr>
<td valign="top">

`deleted_length`

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Total length of the pending deletions

</td>
</tr>
<tr>
<td valign="top">

`last_refresh`

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Date and time of the last refresh

</td>
</tr>
</table>



<a name="loioa5fbd83484f210158d6fe1b9b7331051__iq_iquda_95"/>

## Remarks

Use `sa_text_index_stats` to view statistical information for each TEXT index in the database.

The `pending_length`, `deleted_length`, and `last_refresh` values are NULL for IMMEDIATE REFRESH TEXT indexes.



<a name="loioa5fbd83484f210158d6fe1b9b7331051__iq_iquda_96"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.

Also requires one of the following:

-   MANAGE ANY STATISTICS system privileges
-   CREATE ANY INDEX system privileges
-   ALTER ANY INDEX system privileges
-   DROP ANY INDEX system privileges
-   CREATE ANY OBJECT system privileges
-   ALTER ANY OBJECT system privileges
-   DROP ANY OBJECT system privileges



<a name="loioa5fbd83484f210158d6fe1b9b7331051__section_t1n_lss_mbb"/>

## Side Effects

None



<a name="loioa5fbd83484f210158d6fe1b9b7331051__iq_iquda_97"/>

## Examples

This example uses the sa\_text\_index\_stats system procedure to return statistical information for each TEXT index in the database:

```
CALL sa_text_index_stats( );
```


<table>
<tr>
<th valign="top">

owner\_id

</th>
<th valign="top">

table\_id

</th>
<th valign="top">

index\_id

</th>
<th valign="top">

text\_config\_id

</th>
<th valign="top">

owner\_name

</th>
<th valign="top">

table\_name

</th>
<th valign="top">

index\_name

</th>
</tr>
<tr>
<td valign="top">

103

</td>
<td valign="top">

1792

</td>
<td valign="top">

3

</td>
<td valign="top">

12383

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

PRODUCTS

</td>
<td valign="top">

myTxtIdx

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="6">

\(Continued\)

</th>
</tr>
<tr>
<th valign="top">

text\_config\_name

</th>
<th valign="top">

doc\_count

</th>
<th valign="top">

doc\_length

</th>
<th valign="top">

pending\_length

</th>
<th valign="top">

deleted\_length

</th>
<th valign="top">

last\_refresh

</th>
</tr>
<tr>
<td valign="top">

default\_char

</td>
<td valign="top">

4

</td>
<td valign="top">

32

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
</tr>
</table>

