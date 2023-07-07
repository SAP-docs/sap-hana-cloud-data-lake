<!-- loio817590756ce21014a0abf2e01acdf61e -->

# sa\_get\_bits System Procedure for Data Lake Relational Engine

Takes a bit string and returns a row for each bit in the string. By default, only rows with a bit value of 1 are returned.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_get_bits( 
<bit_string> 
[, <only_on_bits> ] 
)
```



<a name="loio817590756ce21014a0abf2e01acdf61e__sa_get_bits_parm1"/>

## Parameters


<dl>
<dt><b>

 *<bit\_string\>* 

</b></dt>
<dd>

Use this LONG VARBIT parameter to specify the bit string from which to get the bits. If the *<bit\_string\>* parameter is NULL, then no rows are returned.



</dd><dt><b>

 *<only\_on\_bits\>* 

</b></dt>
<dd>

Use this optional BIT parameter to specify whether to return only rows with on bits \(bits with the value of 1\). Specify 1 \(the default\) to return only rows with on bits; specify 0 to return rows for all bits in the bit string.



</dd>
</dl>



<a name="loio817590756ce21014a0abf2e01acdf61e__sa_get_bits_output1"/>

## Column Definitions for Output


<table>
<tr>
<th valign="top">

Column



</th>
<th valign="top">

Data type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

bitnum



</td>
<td valign="top">

UNSIGNED INTEGER



</td>
<td valign="top">

The position of the bit described by this row. For example, the first bit in the bit string has bitnum of 1.



</td>
</tr>
<tr>
<td valign="top">

bit\_val



</td>
<td valign="top">

BIT



</td>
<td valign="top">

The value of the bit at position bitnum. If *<only\_on\_bits\>* is set to 1, this value is always 1.



</td>
</tr>
</table>



<a name="loio817590756ce21014a0abf2e01acdf61e__sa_get_bits_remarks1"/>

## Remarks

The sa\_get\_bits system procedure decodes a bit string, returning one row for each bit in the bit string, indicating the value of the bit. If *<only\_on\_bits\>* is set to 1 \(the default\) or NULL, then only rows corresponding to on bits are returned. An optimization allows this case to be processed efficiently for long bit strings that have few on bits. If *<only\_on\_bits\>* is set to 0, then a row is returned for each bit in the bit string.

For example, the statement `CALL sa_get_bits( '1010' );` returns the following result set, indicating on bits in positions 1 and 3 of the bit string.


<table>
<tr>
<th valign="top">

bitnum



</th>
<th valign="top">

bit\_val



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

1



</td>
</tr>
</table>

The sa\_get\_bits system procedure can be used to convert a bit string into a relation. This procedure can be used to join a bit string with a table, or to retrieve a bit string as a result set instead of as a single binary value. It can be more efficient to retrieve a bit string as a result set if there are a large number of 0 bits, as they don’t need to be retrieved.



<a name="loio817590756ce21014a0abf2e01acdf61e__sa_get_bits_priv1"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on the procedure
-   MONITOR system privilege



<a name="loio817590756ce21014a0abf2e01acdf61e__sa_get_bits_sideeffects1"/>

## Side Effects

None

**Related Information**  


[sa_get_bits System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/dc051ed9b19649ec91efd03e157132cb.html "Takes a bit string and returns a row for each bit in the string. By default, only rows with a bit value of 1 are returned.") :arrow_upper_right:

