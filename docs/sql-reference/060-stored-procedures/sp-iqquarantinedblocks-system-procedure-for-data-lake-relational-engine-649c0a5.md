<!-- loio649c0a5500af44d192fc7e8ac6e3a538 -->

# sp\_iqquarantinedblocks System Procedure for Data Lake Relational Engine

Displays information about block numbers that cannot be reused because they hold corrupt objects, and will remain in use until the corruption is repaired..



<a name="loio649c0a5500af44d192fc7e8ac6e3a538__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqquarantinedblocks
```



<a name="loio649c0a5500af44d192fc7e8ac6e3a538__section_gpx_2kd_4fb"/>

## Parameter

None.



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

sp\_iqquarantinedblocks

</td>
<td valign="top">

A single unsigned bigint column, physicalBlockNumber, one quarantined physical block number per row.

</td>
</tr>
</table>



<a name="loio649c0a5500af44d192fc7e8ac6e3a538__section_m5g_yjd_4fb"/>

## Remarks

A quarantined block is never deallocated and will not be re-used for other objects. A quarantined block remains in use, but inaccessible, by the object that detected the `Incorrect Page Header Read` error that caused it to be marked as quarantined.



<a name="loio649c0a5500af44d192fc7e8ac6e3a538__section_ekd_bld_4fb"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.



<a name="loio649c0a5500af44d192fc7e8ac6e3a538__section_ptp_jjd_4fb"/>

## Side Effects

None.



<a name="loio649c0a5500af44d192fc7e8ac6e3a538__section_on4_bjd_4fb"/>

## Examples

This example retrieves the block numbers in ascending order:

```
SELECT qm.physicalBlockNumber FROM sp_iqquarantinedblocks() AS qm ORDER BY 1;
```

This example counts the number of quarantined blocks:

```
SELECT COUNT(*) FROM sp_iqquarantinedblocks();
```

