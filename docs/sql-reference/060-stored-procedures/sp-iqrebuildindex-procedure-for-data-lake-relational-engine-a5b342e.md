<!-- loioa5b342e484f21015b652c2f5c7685bca -->

# sp\_iqrebuildindex Procedure for Data Lake Relational Engine

Rebuilds column indexes.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqrebuildindex <table_name>, <index_clause>
```



<a name="loioa5b342e484f21015b652c2f5c7685bca__iq_refbb_1720"/>

## Parameter


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

One or more of the following strings, separated by spaces:

```
column <column_name>[<count>]
```

```
index <index_name>
```

You need to specify the keywords column and index. These keywords are not case-sensitive.

> ### Caution:  
> A third-party reference document describes an unsupported sp\_iqrebuildindex syntax. Specifying the table name in the index clause, such as in the following example, results in an error:
> 
> ```
> sp_iqrebuildindex tb1, 'column tb1.c1'
> ```



</dd>
</dl>



<a name="loioa5b342e484f21015b652c2f5c7685bca__iq_refbb_1722"/>

## Remarks

> ### Note:  
> To rebuild an index other than the default FP index, specify the index name. sp\_iqrebuildindex behavior is the same regardless of the `FP_NBIT_IQ15_COMPATIBILITY` setting.

Each *<column\_name\>* or *<index\_name\>* must refer to a column or index on the specified table. If you specify a *<column\_name\>* or *<index\_name\>* multiple times, the procedure returns an error and no index is rebuilt.

The *<count\>* is a non-negative number that represents the IQ UNIQUE value. In a CREATE TABLE statement, `IQ UNIQUE (count)` approximates how many distinct values can be in a given column. The number of distinct values affects query speed and storage requirements.

MERGEALL and RETIER are keywords specific to HG index operations:

```
sp_iqrebuildindex ('<table name>', 'index <index name> [ MERGEALL | RETIER ]')
```

If MERGEALL or RETIER are omitted from an operation from an HG index , sp\_iqrebuildindex truncates and reconstructs the entire HG index from the column data.

MERGEALL merges all tiers of a tiered HG index and moves the contents into an appropriate tier:

```
sp_iqrebuildindex ('<table name>', 'index <index name> MERGEALL')
```

The merge ensures that there is only one active sub-index in a tiered HG index. MERGEALL operations may improve query access time for a tiered index in cases where there are too many deleted records \(as shown by sp\_iqindexmetadata\). MERGEALL will only be supported with an index clause and only if the index specified is an HG index.

RETIER is a keyword specific to HG indexes that changes the format of an HG index from non-tiered HG to tiered HG, or tiered HG to non-tiered HG:

```
sp_iqrebuildindex ('<table name>', 'index <index name> RETIER')
```

`RETIER` toggles the format of an HG index:

-   RETIER converts a tiered HG index into a single non-tiered HG index. Tiering metadata is disabled and only one sub-index is maintained.
-   RETIER converts a non-tiered HG into a tiered HG index, and pushes the single sub-index, which contains all the data into an appropriate tier.

MERGEALL and RETIER will only be supported with an index clause, and only if the index specified is an HG index.

If you specify a column name, sp\_iqrebuildindex rebuilds the default FP index for that column; no index name is needed. If you specify the default FP index name assigned by data lake Relational Engine in addition to the column name, sp\_iqrebuildindex returns an error.

sp\_iqrebuildindex rebuilds a WD index on a column of data type `LONG VARCHAR(CLOB)` .

A column with IQ UNIQUE *<n\>* value determines whether sp\_iqrebuildindex rebuilds the column as Flat FP or NBit. An IQ UNIQUE *<n\>* value set to 0 rebuilds the index as a Flat FP. An *<n\>* value greater than 0 but less than 2,147,483,647 rebuilds the index as NBit. NBit columns without an *<n\>* value are rebuilt as NBit. sp\_iqrebuildindex rebuilds an NBit column as NBit, even if you do not specify a count. If you do specify a count, the *<n\>* value must be greater than the number of unique values already in the index.

If you rebuild a column with a Flat FP index, and the column does not include an IQ UNIQUE *<n\>* value, sp\_iqrebuildindex rebuilds the index as N-Bit FP up to the limits defined in the FP\_NBIT\_AUTOSIZE\_LIMIT and FP\_NBIT\_LOOKUP\_MB options. Specifying an *<n\>* value for a flat column throws an error if FP\_NBIT\_ENFORCE\_LIMITS=ON and the cardinality exceeds the count.

The sp\_iqrebuildindex default interface allows a user to re-create an entire HG index from an existing FP index. sp\_iqrebuildindex re-reads all FP index column values and creates the HG index. This will, however retain all the metadata regarding tier sizes, continuous load size, etc.

> ### Note:  
> This procedure does not support TEXT indexes. To rebuild a TEXT index you must drop and re-create the index.



<a name="loioa5b342e484f21015b652c2f5c7685bca__section_fjr_fy1_tbb"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure along with one of the following:

-   INSERT ANY TABLE system privilege
-   INSERT privilege on the table system privilege



## Side Effects

None



<a name="loioa5b342e484f21015b652c2f5c7685bca__iq_refbb_1723"/>

## Examples

-   The following two lines of syntax show the default FP index on column dept\_id:

    ```
    sp_iqrebuildindex 'emp1', 'column dept_id'
    
    call sp_iqrebuildindex ('empl1', 'column dept_id')
    ```

-   This creates a flat FP index on column c1:

    ```
    CREATE TABLE mytable (c1 int IQ UNIQUE (0))
    ```

-   The following two converts the default Flat FP index to an Nbit index with an estimated distinct count of 1024:

    ```
    sp_iqrebuildindex 'mytable', 'column c1 1024'
    
    call sp_iqrebuildindex ('mytable', 'column c1 1024')
    ```

    > ### Note:  
    > Users can expect to see a temporary performance drop when sp\_iqrebuildindex runs on a large HG index.


**Related Information**  


[sp\_iqindexfragmentation Procedure for Data Lake Relational Engine](sp-iqindexfragmentation-procedure-for-data-lake-relational-engine-a5ac10a.md "Reports information about the percentage of page space taken up within the B-trees, garrays, and bitmap structures in data lake Relational Engine indexes.")

[sp\_iqrowdensity Procedure for Data Lake Relational Engine](sp-iqrowdensity-procedure-for-data-lake-relational-engine-a5b5cb9.md "Reports information about the internal row fragmentation for a table at the FP index level.")

