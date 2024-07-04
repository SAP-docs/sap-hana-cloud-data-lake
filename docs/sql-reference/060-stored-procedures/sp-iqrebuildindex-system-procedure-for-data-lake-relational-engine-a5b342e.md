<!-- loioa5b342e484f21015b652c2f5c7685bca -->

# sp\_iqrebuildindex System Procedure for Data Lake Relational Engine

Rebuilds column indexes.



<a name="loioa5b342e484f21015b652c2f5c7685bca__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqrebuildindex ('[ { <owner> | <schema-name> }.]<table_name>', '<index_clause>'
   [ { MERGEALL | RETIER })
```



<a name="loioa5b342e484f21015b652c2f5c7685bca__iq_refbb_1720"/>

## Parameters


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Partial or fully qualified table name on which the index rebuild process takes place. If the user both owns the table and executes the procedure, a partially qualified name may be used; otherwise, the table name must be fully qualified.



</dd><dt><b>

*<index\_clause\>*

</b></dt>
<dd>

Specify the type of type of index clause.

```
<index_clause> ::=
   { [ COLUMN <column_name> [ <count> ] ]
     [ INDEX <index_name> ] }
```

You can specify multiple clauses of different types, separated by spaces as long as they all reference the same table. For example:

```
CALL sp_iqrebuildindex ('T1', 'INDEX ASIQ_IDX_T1729_C2_FP INDEX index_a1 COLUMN a COLUMN b'
```

INDEX and COLUMN are case insensitive. Do not include the *<table\_name\>* in the *<index\_clause\>*.



</dd><dt><b>

MERGEALL | RETIER

</b></dt>
<dd>

MERGEALL and RETIER are keywords specific to HG index operations: If MERGEALL or RETIER are omitted from an operation from an HG index , sp\_iqrebuildindex truncates and reconstructs the entire HG index from the column data.

MERGEALL merges all tiers of a tiered HG index and moves the contents into an appropriate tier. The merge ensures that there is only one active sub-index in a tiered HG index. MERGEALL operations may improve query access time for a tiered index in cases where there are too many deleted records \(as shown by sp\_iqindexmetadata\). MERGEALL is only supported with an INDEX clause and only if the index specified is an HG index.

RETIER is a keyword specific to HG indexes that toggles the format of an HG index from non-tiered HG to tiered HG, or tiered HG to non-tiered HG. When converting a tiered HG index into a single non-tiered HG index, tiering metadata is disabled and only one sub-index is maintained. When converting a non-tiered HG index into a tiered HG index, it pushes the single sub-index, which contains all the data into an appropriate tier. MERGEALL and RETIER are only supported with an index clause, and only if the index specified is an HG index.



</dd>
</dl>



<a name="loioa5b342e484f21015b652c2f5c7685bca__section_zny_wbd_fbc"/>

## Result Set

None.



<a name="loioa5b342e484f21015b652c2f5c7685bca__iq_refbb_1722"/>

## Remarks

> ### Note:  
> This procedure does not support TEXT indexes. To rebuild a TEXT index you must drop and re-create the index.

Expect to see a temporary performance drop when sp\_iqrebuildindex runs on a large HG index.

To rebuild an index other than the default FP index, specify the index name. sp\_iqrebuildindex behavior is the same regardless of the `FP_NBIT_IQ15_COMPATIBILITY` setting.

Each *<column\_name\>* or *<index\_name\>* must refer to a column or index on the specified table. If you specify a *<column\_name\>* or *<index\_name\>* multiple times, the procedure returns an error and no index is rebuilt.

The *<count\>* is a non-negative number that represents the IQ UNIQUE value. In a CREATE TABLE statement, `IQ UNIQUE (count)` approximates how many distinct values can be in a given column. The number of distinct values affects query speed and storage requirements.

If you specify a column name, sp\_iqrebuildindex rebuilds the default FP index for that column; no index name is needed. If you specify the default FP index name assigned by data lake Relational Engine in addition to the column name, sp\_iqrebuildindex returns an error.

sp\_iqrebuildindex rebuilds a WD index on a column of data type `LONG VARCHAR(CLOB)` .

A column with IQ UNIQUE *<n\>* value determines whether sp\_iqrebuildindex rebuilds the column as Flat FP or NBit. An IQ UNIQUE *<n\>* value set to 0 rebuilds the index as a Flat FP. An *<n\>* value greater than 0 but less than 2,147,483,647 rebuilds the index as NBit. NBit columns without an *<n\>* value are rebuilt as NBit. sp\_iqrebuildindex rebuilds an NBit column as NBit, even if you do not specify a count. If you do specify a count, the *<n\>* value must be greater than the number of unique values already in the index.

If you rebuild a column with a Flat FP index, and the column does not include an IQ UNIQUE *<n\>* value, sp\_iqrebuildindex rebuilds the index as N-Bit FP up to the limits defined in the FP\_NBIT\_AUTOSIZE\_LIMIT and FP\_NBIT\_LOOKUP\_MB options. Specifying an *<n\>* value for a flat column throws an error if FP\_NBIT\_ENFORCE\_LIMITS=ON and the cardinality exceeds the count.

The sp\_iqrebuildindex default interface allows a user to re-create an entire HG index from an existing FP index. sp\_iqrebuildindex re-reads all FP index column values and creates the HG index. This will, however retain all the metadata regarding tier sizes, continuous load size, etc.



<a name="loioa5b342e484f21015b652c2f5c7685bca__section_fjr_fy1_tbb"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure, along with one of the following:

-   You own the underlying table.
-   INSERT ANY TABLE system privilege
-   INSERT object-level privilege on the underlying table



## Side Effects

None.



<a name="loioa5b342e484f21015b652c2f5c7685bca__iq_refbb_1723"/>

## Examples

This example rebuilds the index on column dept\_id in table empl1.

```
CALL sp_iqrebuildindex ('empl1', 'COLUMN dept_id');
```

This example rebuilds the indexes ASIQ\_IDX\_T1729\_C2\_FP and index\_a1 and the index on column A.

```
CALL sp_iqrebuildindex ('customer1',INDEX ASIQ_IDX_T1729_C2_FP INDEX index_a1 COLUMN a'
 'COLUMN c1 1024');
```

This example converts the default Flat FP index to an Nbit index on column c1 with an estimated distinct count of 1024.

```
CALL sp_iqrebuildindex ('mytable', 'COLUMN c1 1024');
```

This example merges all tiers of a tiered HG index and moves the contents into an appropriate tier.

```
CALL sp_iqrebuildindex ('T1', 'INDEX index_T1 MERGEALL');
```

This example changes the format of an HG index from non-tiered HG to tiered HG, or tiered HG to non-tiered HG.

```
CALL sp_iqrebuildindex ('T2', 'INDEX index_T2 RETIER');
```

**Related Information**  


[sp\_iqindexfragmentation System Procedure for Data Lake Relational Engine](sp-iqindexfragmentation-system-procedure-for-data-lake-relational-engine-a5ac10a.md "Reports information about the percentage of page space taken up within the B-trees, garrays, and bitmap structures in data lake Relational Engine indexes.")

[sp\_iqrowdensity System Procedure for Data Lake Relational Engine](sp-iqrowdensity-system-procedure-for-data-lake-relational-engine-a5b5cb9.md "Reports information about the internal row fragmentation for a table at the FP index level.")

