<!-- loioa5fd29ba84f210159cb498816176a030 -->

# sp\_iqshowcompression System Procedure for Data Lake Relational Engine

Displays compression settings for columns of LONG BINARY \(BLOB\) and LONG VARCHAR \(CLOB\) data types.



<a name="loioa5fd29ba84f210159cb498816176a030__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqshowcompression ( <owner>, <table>, <column> )
```



<a name="loioa5fd29ba84f210159cb498816176a030__iq_iquda_120"/>

## Parameters


<dl>
<dt><b>

*<owner\>*

</b></dt>
<dd>

The owner of the table for which you are setting compression.



</dd><dt><b>

*<table\>*

</b></dt>
<dd>

The table for which you are setting compression.



</dd><dt><b>

*<column\>*

</b></dt>
<dd>

The column for which you are setting compression.



</dd>
</dl>



<a name="loioa5fd29ba84f210159cb498816176a030__iq_iquda_122"/>

## Result Set


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Column

</td>
<td valign="top">

Name of the column displayed.

</td>
</tr>
<tr>
<td valign="top">

Compression

</td>
<td valign="top">

Compression setting values are 'ON' \(compression enabled\) and 'OFF' \(compression disabled\).

</td>
</tr>
</table>



<a name="loioa5fd29ba84f210159cb498816176a030__iq_iquda_121"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure. If you do not own the underlying tables, you also need one of the following:

-   ALTER ANY TABLE system privilege
-   ALTER ANY OBJECT system privilege



## Side Effects

None.



<a name="loioa5fd29ba84f210159cb498816176a030__iq_iquda_124"/>

## Examples

Assume table T1, which contains Col1 and Col2 is owned by USER1.

This example returns the compression setting on Col1.

```
CALL sp_iqshowcompression('USER1', 'T1', 'Col1');
```


<table>
<tr>
<th valign="top">

Column

</th>
<th valign="top">

Compression

</th>
</tr>
<tr>
<td valign="top">

Col1

</td>
<td valign="top">

OFF

</td>
</tr>
</table>

