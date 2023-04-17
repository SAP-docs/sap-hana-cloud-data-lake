<!-- loiodc051ed9b19649ec91efd03e157132cb -->

# sa\_get\_bits System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Takes a bit string and returns a row for each bit in the string. By default, only rows with a bit value of 1 are returned.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Running Procedures](remote-execute-usage-examples-for-running-procedures-3e7f86d.md) for more information.



```
sa_get_bits( 
<bit_string> 
[, <only_on_bits> ] 
)
```



<a name="loiodc051ed9b19649ec91efd03e157132cb__section_qh1_f3d_srb"/>

## Parameters

  *<bit\_string\>* 
 :   Use this LONG VARBIT parameter to specify the bit string from which to get the bits. If the *<bit\_string\>* parameter is NULL, then no rows are returned.

   *<only\_on\_bits\>* 
 :   Use this optional BIT parameter to specify whether to return only rows with on bits \(bits with the value of 1\). Specify 1 \(the default\) to return only rows with on bits; specify 0 to return rows for all bits in the bit string.

 

<a name="loiodc051ed9b19649ec91efd03e157132cb__section_ej1_23d_srb"/>

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



<a name="loiodc051ed9b19649ec91efd03e157132cb__section_kqw_c3d_srb"/>

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



<a name="loiodc051ed9b19649ec91efd03e157132cb__section_u51_bkf_3jb"/>

## Permissions

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loiodc051ed9b19649ec91efd03e157132cb__section_svb_c3d_srb"/>

## Side Effects

None

**Related Information**  


[CREATE VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/create-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-4d41128.md "Creates a view on the database. Views are used to give a different perspective on the data even though it is not stored that way.")

[sa_get_bits System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/817590756ce21014a0abf2e01acdf61e.html "Takes a bit string and returns a row for each bit in the string. By default, only rows with a bit value of 1 are returned.") :arrow_upper_right:

