<!-- loioa5fc07d584f21015b6b0d8b56823c3e0 -->

# sa\_text\_index\_vocab System Procedure for Data Lake Relational Engine

Lists all terms that appear in a TEXT index, and the total number of indexed values in which each term appears.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_text_index_vocab (
	'<text-index-name>',
	'<table-name>',
	'<table-owner>'
	)
```



<a name="loioa5fc07d584f21015b6b0d8b56823c3e0__iq_iquda_99"/>

## Parameters

 *<text-index-name\>*
 :   A CHAR\(128\) parameter that specifies the name of the TEXT index.

  *<table-name\>*
 :   A CHAR\(128\) parameter that specifies the name of the table on which the TEXT index is built.

  *<table-owner\>*
 :   A CHAR\(128\) parameter that specifies the owner of the table.

 

<a name="loioa5fc07d584f21015b6b0d8b56823c3e0__iq_iquda_101"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). You must also have one of the following:

-   SELECT ANY TABLE system privilege
-   SELECT privilege on the indexed table



<a name="loioa5fc07d584f21015b6b0d8b56823c3e0__iq_iquda_100"/>

## Remarks

`sa_text_index_vocab` returns all terms that appear in a TEXT index, and the total number of indexed values in which each term appears \(which is less than the total number of occurrences, if the term appears multiple times in some indexed values\).

Parameter values cannot be host variables or expressions. The arguments *<text-index-name\>*, *<table-name\>*, and *<table-owner\>* must be constraints or variables.



<a name="loioa5fc07d584f21015b6b0d8b56823c3e0__section_dhd_mrs_mbb"/>

## Side Effects

None



<a name="loioa5fc07d584f21015b6b0d8b56823c3e0__iq_iquda_102"/>

## Example

The following example executes `sa_text_index_vocab` to return all the terms that appear in the TEXT index `MyTextIndex` on table `Customers` owned by `GROUPO`:

```
sa_text_index_vocab
('MyTextIndex','Customers','GROUPO');
```

Terms in the index are:


<table>
<tr>
<th valign="top" rowspan="1">

Term



</th>
<th valign="top" rowspan="1">

Frequency



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

a



</td>
<td valign="top" rowspan="1">

1



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Able



</td>
<td valign="top" rowspan="1">

1



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Acres



</td>
<td valign="top" rowspan="1">

1



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Active



</td>
<td valign="top" rowspan="1">

5



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Advertising



</td>
<td valign="top" rowspan="1">

1



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Again



</td>
<td valign="top" rowspan="1">

1



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

...



</td>
<td valign="top" rowspan="1">

...



</td>
</tr>
</table>

