<!-- loio649c0a5500af44d192fc7e8ac6e3a538 -->

# sp\_iqquarantinedblocks Procedure for Data Lake Relational Engine

Displays information about block numbers that cannot be reused because they hold corrupt objects, and will remain in use until the corruption is repaired..



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqquarantinedblocks
```



<a name="loio649c0a5500af44d192fc7e8ac6e3a538__section_gpx_2kd_4fb"/>

## Parameter

None.



## Returns

A single unsigned bigint column, physicalBlockNumber, one quarantined physical block number per row.



<a name="loio649c0a5500af44d192fc7e8ac6e3a538__section_m5g_yjd_4fb"/>

## Remarks

A quarantined block is never deallocated and will not be re-used for other objects. A quarantined block remains in use, but inaccessible, by the object that detected the `Incorrect Page Header Read` error that caused it to be marked as quarantined.



<a name="loio649c0a5500af44d192fc7e8ac6e3a538__section_ekd_bld_4fb"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md).



<a name="loio649c0a5500af44d192fc7e8ac6e3a538__section_ptp_jjd_4fb"/>

## Side Effects

None



<a name="loio649c0a5500af44d192fc7e8ac6e3a538__section_on4_bjd_4fb"/>

## Examples

-   This example retrieves the block numbers in ascending order:

    ```
    SELECT qm.physicalBlockNumber FROM sp_iqquarantinedblocks() AS qm ORDER BY 1
    ```

-   This example counts the number of quarantined blocks:

    ```
    SELECT COUNT(*) FROM sp_iqquarantinedblocks()
    ```


