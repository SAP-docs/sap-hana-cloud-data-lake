<!-- loioa87db4e784f2101596f1b7355fcd2137 -->

# sp\_iqindexrebuildwidedata System Procedure for Data Lake Relational Engine

Identifies wide columns in migrated databases that you need to rebuild before they are available for read/write activities.



<a name="loioa87db4e784f2101596f1b7355fcd2137__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqindexrebuildwidedata ( [ '<table_name>' ] )
```



<a name="loioa87db4e784f2101596f1b7355fcd2137__section_hjl_dbz_mbb"/>

## Parameters


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Include the optional *<table\_name\>* parameter to generate a list of wide columns for that table. Omit the *<table\_name\>* parameter to generate a list of wide columns for all tables in the database.



</dd>
</dl>



<a name="loioa87db4e784f2101596f1b7355fcd2137__section_iyd_vfx_c1c"/>

## Result Set

See Examples.



<a name="loioa87db4e784f2101596f1b7355fcd2137__section_xj5_z1z_mbb"/>

## Remarks

CHAR, VARCHAR, BINARY, and VARBINARY columns wider than 255 characters, as well as all LONG VARCHAR and LONG BINARY columns in databases migrated to data lake Relational Engine must be rebuilt before the database engine can perform read/write activities on them. sp\_iqindexrebuildwidedata identifies these columns and generates a list of statements that you can use to rebuild the columns with the sp\_iqrebuildindex procedure.



## Privileges

Requires EXECUTE object-level privilege on this procedure along with one of the following:

-   You own the object referenced by the procedure.
-   INSERT object-level privilege on the table



## Side Effects

None



## Examples

This example generates wide-column rebuild statements for table T2:

```
CALL sp_iqindexrebuildwidedata ('T2');
```


<table>
<tr>
<th valign="top">

Owner

</th>
<th valign="top">

Table

</th>
<th valign="top">

Column

</th>
<th valign="top">

Domain

</th>
<th valign="top">

Width

</th>
<th valign="top">

IndexType

</th>
<th valign="top">

sp\_iqrebuild

</th>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

T2

</td>
<td valign="top">

C1

</td>
<td valign="top">

char

</td>
<td valign="top">

1020

</td>
<td valign="top">

Long varchar FP

</td>
<td valign="top">

sp\_iqrebuildindex '"USER1.T2"' 'column"C1" 0';

</td>
</tr>
</table>

