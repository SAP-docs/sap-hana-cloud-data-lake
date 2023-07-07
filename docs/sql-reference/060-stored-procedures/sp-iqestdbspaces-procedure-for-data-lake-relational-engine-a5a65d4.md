<!-- loioa5a65d4e84f21015a001ad34c7f759fe -->

# sp\_iqestdbspaces Procedure for Data Lake Relational Engine

Estimates the number and size of dbspaces needed for a given total index size.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqestdbspaces ( <db_size_in_bytes>, <iq_page_size>,
<min_#_of_bytes>, <max_#_of_bytes> )
```



<a name="loioa5a65d4e84f21015a001ad34c7f759fe__section_kck_hnz_mbb"/>

## Parameters


<dl>
<dt><b>

*<db\_size\_in\_bytes\>*

</b></dt>
<dd>

A DECIMAL\(16\) parameter that specifies the size of the database in bytes.



</dd><dt><b>

*<iq\_page\_size\>*

</b></dt>
<dd>

A SMALLINT parameter that specifies the page size defined for the data lake Relational Engine segment of the database \(must be a power of 2 between 65536 and 524288; the default is 131072\).



</dd><dt><b>

*<min\_\#\_of\_bytes\>*

</b></dt>
<dd>

An INT parameter that specifies the minimum number of bytes per dbspace segment. The default is 20,000,000 \(20 MB\).



</dd><dt><b>

*<max\_\#\_of\_bytes\>*

</b></dt>
<dd>

An INT parameter that specifies the maximum number of bytes per dbspace segment. The default is 2,146,304,000 \(2.146 GB\).



</dd>
</dl>



<a name="loioa5a65d4e84f21015a001ad34c7f759fe__iq_refbb_1554"/>

## Remarks

`sp_iqestdbspaces` reports several recommendations, depending on how much of the data is unique:

-   min – if there is little variation in data, you can choose to create only the dbspace segments of the sizes recommended as min. These recommendations reflect the best possible compression on data with the least possible variation.
-   avg – if your data has an average amount of variation, create the dbspace segments recommended as min, plus additional segments of the sizes recommended as avg.
-   max – if your data has a high degree of variation \(many unique values\), create the dbspace segments recommended as min, avg, and max.
-   spare – if you are uncertain about the number of unique values in your data, create the dbspace segments recommended as min, avg, max, and spare. You can always delete unused segments after loading your data, but creating too few can cost you some time.

Displays information about the number and size of dbspace segments based on the size of the database, the data lake Relational Engine page size, and the range of bytes per dbspace segment. This procedure assumes that the database was created with the default block size for the specified data lake Relational Engine page size; otherwise, the returned estimated values are incorrect.



<a name="loioa5a65d4e84f21015a001ad34c7f759fe__iq_refbb_1552"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with the MANAGE ANY DBSPACE system privilege.



## Side Effects

None



<a name="loioa5a65d4e84f21015a001ad34c7f759fe__section_yh2_12f_nbb"/>

## Example

This following example estimates the size and number of dbspace segments needed for a 12 GB database:

```
sp_iqestdbspaces 12000000000, 65536, 500000000, 2146304000
```


<table>
<tr>
<th valign="top" rowspan="1">

dbspace files



</th>
<th valign="top" rowspan="1">

Type



</th>
<th valign="top" rowspan="1">

            Size



</th>
<th valign="top" rowspan="1">

Msg



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

                 1



</td>
<td valign="top" rowspan="1">

min



</td>
<td valign="top" rowspan="1">

2146304000



</td>
<td valign="top" rowspan="1">



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

                 2



</td>
<td valign="top" rowspan="1">

min



</td>
<td valign="top" rowspan="1">

2146304000



</td>
<td valign="top" rowspan="1">



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

                 3



</td>
<td valign="top" rowspan="1">

min



</td>
<td valign="top" rowspan="1">

  507392000



</td>
<td valign="top" rowspan="1">



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

                 4



</td>
<td valign="top" rowspan="1">

avg



</td>
<td valign="top" rowspan="1">

2146304000



</td>
<td valign="top" rowspan="1">



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

                 5



</td>
<td valign="top" rowspan="1">

max



</td>
<td valign="top" rowspan="1">

2053697536



</td>
<td valign="top" rowspan="1">



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

                 6



</td>
<td valign="top" rowspan="1">

spare



</td>
<td valign="top" rowspan="1">

1200001024



</td>
<td valign="top" rowspan="1">



</td>
</tr>
</table>

You should create a minimum of three segments \(listed as `min`\) for the best compression, if you expect little uniqueness in the data. If the data has an average amount of variation, create one more segment \(listed as `avg`\). Data with a lot of variation \(many unique values, requiring extensive indexing\), may require an additional segment \(listed as `max`\). You can ensure that your initial load succeeds by creating a spare segment of 1200001024 bytes. Once you have loaded the database, you can delete any unused dbspace segments.

