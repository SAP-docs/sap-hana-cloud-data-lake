<!-- loioa59d2e0484f21015922aa8b764f89495 -->

# sp\_iqcheckdb Procedure for Data Lake Relational Engine

Checks validity of the current database. Optionally corrects allocation problems for dbspaces or databases. sp\_iqcheckdb does not check a partitioned table if partitioned data exists on offline dbspaces.



```
sp_iqcheckdb '<mode> <target> [ … ] [ resources <resource-percent> ]'
```

```
<mode> ::=
   { allocation 
   | check 
   | verify }
```

```
<target> ::=
   [ indextype <index-type> […] ]  database 
   | { [ indextype <index-type> ] […] table <table-name> [ partition <partition-name> ] […] 
   | index <index-name> 
   |  […] dbspace <dbspace-name>}
   | cache <main-cache-name>
```



<a name="loioa59d2e0484f21015922aa8b764f89495__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

database

</b></dt>
<dd>

If the target is a database, all dbspaces must be online.



</dd><dt><b>

*<index-type\>*

</b></dt>
<dd>

One of the following index types: FP, CMP, HG, WD, DATE, TIME, DTTM, TEXT.

If the specified *<index-type\>* does not exist in the target, an error message is returned. If multiple index types are specified and the target contains only some of these index types, the existing index types are processed by sp\_iqcheckdb.



</dd><dt><b>

*<index-name\>*

</b></dt>
<dd>

May contain owner and table qualifiers: \[\[*<owner\>*.\]*<table-name\>*.\]*<index-name\>*.

If *<owner\>* is not specified, current user and database owner \(`dbo`\) are substituted in that order. If *<table\>* is not specified, *<index-name\>* must be unique.



</dd><dt><b>

*<table-name\>*

</b></dt>
<dd>

May contain an owner qualifier: <code>[<i class="varname">&lt;owner&gt;</i>.]<i class="varname">&lt;table-name&gt;</i>.</code>

If *<owner\>* is not specified, current user and database owner \(dbo\) are substituted in that order. *<table-name\>* cannot be a temporary or pre-join table.

> ### Note:  
> If either the table name or the index name contains spaces, enclose the *<table-name\>* or *<index-name\>* parameter in double quotation marks:
> 
> ```
> sp_iqcheckdb 'check index "dbo.sstab.i2" resources 75'
> ```



</dd><dt><b>

*<partition-name\>*

</b></dt>
<dd>

The *<partition-name\>* parameter contains no qualifiers. If it contains spaces, enclose it in double quotation marks.

The partition filter causes `sp_iqcheckdb` to examine a subset of the corresponding table’s rows that belong to that partition. A partition filter on a table and table target without the partition filter are semantically equivalent when the table has only one partition.



</dd><dt><b>

*<dbspace-name\>*

</b></dt>
<dd>

The *<dbspace-name\>* parameter contains no qualifiers. If it contains spaces, enclose it in double quotation marks.

The dbspace target examines a subset of the database's pages that belong to that dbspace. The dbspace must be online. The dbspace and database target are semantically equivalent when the table has only one dbspace.



</dd><dt><b>

*<resource-percent\>*

</b></dt>
<dd>

The input parameter *<resource-percent\>* must be an integer greater than zero. The resources percentage allows you to limit the CPU utilization of the database consistency checker by controlling the number of threads with respect to the number of CPUs. If *<resource-percent\>* is 100 \(the default value\), then one thread is created per CPU. If *<resource-percent\>* is greater than 100, then there are more threads than CPUs, which might increase performance for some machine configurations. The minimum number of threads is 1.



</dd><dt><b>

*<main-cache-name\>*

</b></dt>
<dd>

The cache target compares pages in the main cache against the original pages in the data lake Relational Engine main store.



</dd>
</dl>

> ### Note:  
> The sp\_iqcheckdb parameter string must be enclosed in single quotes and cannot be greater than 255 bytes in length.



<a name="loioa59d2e0484f21015922aa8b764f89495__IQ_Remarks"/>

## Remarks

sp\_iqcheckdb reads all storage in the database. On successful completion, the database free list \(an internal allocation map\) is updated to reflect the true storage allocation for the database. sp\_iqcheckdb then generates a report listing the actions it has performed.

If an error is found, sp\_iqcheckdb reports the name of the object and the type of error. sp\_iqcheckdb does not update the free list if errors are detected.

sp\_iqcheckdb also allows you to check the consistency of a specified table, index, index type, or the entire database.

> ### Note:  
> sp\_iqcheckdb is the user interface to the data lake Relational Engine database consistency checker \(DBCC\) and is sometimes referred to as DBCC.

There are three modes for checking database consistency, and one for resetting allocation maps. If mode and target are not both specified in the parameter string, data lake Relational Engine returns the error message:

```
Could not execute 'sp_iqcheckdb' Error: (dberror) [-1000276]: At least one mode and target must be specified. – (dblib/db_dbcc.cxx 1459)
```

sp\_iqcheckdb checks the allocation of every block in the database and saves the information in the current session until the next sp\_iqdbstatistics procedure is issued. sp\_iqdbstatistics displays the latest result from the most recent execution of sp\_iqcheckdb.

sp\_iqcheckdb can perform several different functions, depending on the parameters specified.


<table>
<tr>
<th valign="top">

Mode

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Allocation

</td>
<td valign="top">

Checks allocation with blockmap information for the entire database, a specific index, a specific index type, a specific partition, specific table, or a specific dbspace. Does not check index consistency.

Detects duplicate blocks \(blocks for which two or more objects claim ownership\) or extra blocks \(unallocated blocks owned by an object\).

> ### Note:  
> If sp\_iqcheckdb detects a block ownership conflict, it adds a ***\*\*Blocks with Multiple Owners\*\*\**** section to the report, listing the implicated object names and physical block numbers. Block ownership conflicts are only analyzed if the target of sp\_iqcheckdb is either a database or a dbspace. Example of a block ownership conflict:
> 
> ```
> ** Blocks with Multiple Owners                       ****** 
> ** DBA.dupowned1.ASIQ_IDX_T1707_C1_FP    411552      ****** 
> ** DBA.dupowned2.ASIQ_IDX_T1708_C1_FP    411552      ****** 
> ** DBA.dupowned1.ASIQ_IDX_T1707_C1_FP    411553      ****** 
> ...
> ```
> 
> This section of the report can help you recover from corruption caused by block ownership conflicts.Contact SAP Support for advice on how to resolve the reported conflicts.

Detects leaked blocks \(allocated blocks unclaimed by any object in the specified target\) for database or dbspace targets.

When the target is a partitioned table, allocation mode:

-   Checks metadata of all the table’s partition allocation bitmaps
-   Checks metadata of the tables allocation bitmap
-   Verifies that blockmap entries are consistent with the table’s allocation bitmap
-   Verifies that none of the table’s partition allocation bitmaps overlap
-   Checks that rows defined in the table’s partition allocation bitmaps form a superset of the table’s existence bitmap
-   Checks that rows defined in the table’s partition allocation bitmaps form a superset of the table’s allocation bitmap
-   Verifies that the main cache pages are consistent with the data lake Relational Engine main store pages.

> ### Note:  
> sp\_iqcheckdb cannot check all allocation problems if you specify the name of a single index, index type, or table in the input parameter string.

Run in allocation mode:

-   To detect duplicate or unowned blocks \(use database or specific tables or indexes as the target\)
-   If you encounter page header errors



</td>
</tr>
<tr>
<td valign="top">

Check

</td>
<td valign="top">

Verifies that all database pages can be read for the entire database, main cache, specific index, specific index type, specific table, specific partition, or specific dbspace. If the table is partitioned, then check mode will check the table’s partition allocation bitmaps.

Run in check mode if metadata, null count, or distinct count errors are returned when running a query.

</td>
</tr>
<tr>
<td valign="top">

Verify

</td>
<td valign="top">

Verifies the contents of non-FP indexes with their corresponding FP indexes for the entire database, main cache, a specific index, a specific index type, specific table, specific partition, or specific dbspace. If the specified target contains all data pages for the FP and corresponding non-FP indexes, then verify mode detects the following inconsistencies:

-   Missing key – a key that exists in the FP but not in the non-FP index.
-   Extra key – a key that exists in the non-FP index but not in the FP index.
-   Missing row – a row that exists in the FP but not in the non-FP index.
-   Extra row – a row that exists in the non-FP index but not in the FP index.

If the specified target contains only a subset of the FP pages, then verify mode can detect only the following inconsistencies:

-   Missing key
-   Missing row

If the target is a partitioned table, then verify mode also verifies that each row in the table or table partition has been assigned to the correct partition.

Run in verify mode if metadata, null count, or distinct count errors are returned when running a query.

> ### Note:  
> sp\_iqcheckdb does not check referential integrity or repair referential integrity violations.



</td>
</tr>
</table>



### DBCC Performance

The execution time of DBCC varies, depending on the size of the database for an entire database check, the number of tables or indexes specified, and the size of the machine. Checking only a subset of the database \(that is, only specified tables, indexes, or index types\) requires less time than checking an entire database.

This table summarizes the actions and output of the four sp\_iqcheckdb modes.


<table>
<tr>
<th valign="top">

Mode

</th>
<th valign="top">

Errors Detected

</th>
<th valign="top">

Output

</th>
<th valign="top">

Speed

</th>
</tr>
<tr>
<td valign="top">

Allocation

</td>
<td valign="top">

Allocation errors

</td>
<td valign="top">

Allocation statistics only

</td>
<td valign="top">

4 TB per hour

</td>
</tr>
<tr>
<td valign="top">

Check

</td>
<td valign="top">

Allocation errors

Most index errors

</td>
<td valign="top">

All available statistics

</td>
<td valign="top">

60 GB per hour

</td>
</tr>
<tr>
<td valign="top">

Verify

</td>
<td valign="top">

Allocation errors

All index errors

</td>
<td valign="top">

All available statistics

</td>
<td valign="top">

15 GB per hour

</td>
</tr>
</table>



### Output

Depending on the execution mode, sp\_iqcheckdb output includes summary results, errors, informational statistics, and repair statistics. The output may contain as many as three results sets, if you specify multiple modes in a single session. Error statistics are indicated by asterisks \(\*\*\*\*\*\), and appear only if errors are detected.

The output of sp\_iqcheckdb is also copied to the data lake Relational Engine message file `.iqmsg`. If the DBCC\_LOG\_PROGRESS option is ON, sp\_iqcheckdb sends progress messages to the data lake Relational Engine message file, allowing the user to follow the progress of the DBCC operation as it executes.



<a name="loioa59d2e0484f21015922aa8b764f89495__IQ_Privileges"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



<a name="loioa59d2e0484f21015922aa8b764f89495__IQ_Side_Effects"/>

## Side Effects

None



<a name="loioa59d2e0484f21015922aa8b764f89495__IQ_Examples"/>

## Examples

-   Checks the allocation for the entire database:

    ```
    sp_iqcheckdb 'allocation database';
    ```

-   Performs a detailed check on indexes i1, i2, and dbo.t1.i3. If you do not specify a new mode, sp\_iqcheckdb applies the same mode to the remaining targets, as shown in the following command:

    ```
    sp_iqcheckdb 'verify index i1 index i2 index dbo.t1.i3';
    ```

-   You can combine all modes and run multiple checks on a database in a single session. Perform a quick check of partition p1 in table t2, a detailed check of index i1, and allocation checking for the entire database using half of the CPUs:

    ```
    sp_iqcheckdb 'check table t2 partition p1 verify index i1
    allocation database resources 50';
    ```

-   Checks all indexes of the type FP in the database:

    ```
    sp_iqcheckdb 'check indextype FP database';
    ```

-   Verifies the FP and HG indexes in the table t1 and the HNG indexes in the table t2:

    ```
    sp_iqcheckdb 'verify indextype FP indextype HG table t1 indextype HNG table t2';
    ```

-   Check for LVC cell inconsistencies:

    ```
    sp_iqcheckdb 'check index EFG2JKL.ASIQ_IDX_T208_C504_FP';
    ------------------------------------
    Index Statistics:
    ** Inconsistent Index: abcd.EFG2JKL.ASIQ_IDX_T208_C504_FP ****** FP
    Indexes Checked: 1
    ** Unowned LVC Cells: 212 ******
    ```

    The sp\_iqcheckdb LVC cells messages include:

    -   Unowned LVC cells
    -   Duplicate LVC cell rows
    -   Unallocated LVC cell rows

    These messages indicate inconsistencies with a VARCHAR, VARBINARY, LONG BINARY \(BLOB\), or LONG VARCHAR \(CLOB\) column. Unowned LVC cells represent a small amount of unusable storage space and can safely be ignored. Duplicate and Unallocated LVC cells are serious errors that can be resolved only by dropping the damaged columns.

    To drop a damaged column, create a new column from a copy of the old column, then drop the original column and rename the new column to the old column.

    > ### Note:  
    > LVC is a VARCHAR or VARBINARY column with a width greater than 255. LONG BINARY \(BLOB\) and LONG VARCHAR \(CLOB\) also use LVC.

-   Run sp\_iqcheckdb 'allocation database':

    ```
    ===================================================================
    DBCC Allocation Mode Report 
    ===================================================================
       DBCC Status                                    No Errors Detected 
    ===================================================================
    Allocation Summary
    =================================================================== 
       Blocks Total                                   25600
       Blocks in Current Version                      5917
       Blocks in All Versions                         5917
       Blocks in Use                                  5917
       % Blocks in Use                                23  
    ===================================================================
    Allocation Statistics
    ===================================================================
       Marked Logical Blocks                          8320
       Marked Physical Blocks                         5917
       Marked Pages                                   520 
       Blocks in Freelist                             2071196 
       Imaginary Blocks                               2014079 
       Highest PBN in Use                             1049285  
       Total Free Blocks                              19683 
       Usable Free Blocks                             19382
       % Total Space Fragmented                       1 
       % Free Space Fragmented                        1  
       Max Blocks Per Page                            16 
       1  Block Page Count                            165
       3  Block Page Count                            200 
       4  Block Page Count                            1    
       10 Block Page Count                            1 
       16 Block Page Count                            153 
       2  Block Hole Count                            1      
       3  Block Hole Count                            19   
       6  Block Hole Count                            12    
       7  Block Hole Count                            1    
       10 Block Hole Count                            1   
       15 Block Hole Count                            1  
       16 Block Hole Count                            1220 
    
    Partition Summary    
       Database Objects Checked                       2
       Blockmap Identity Count                        2 
       Bitmap Count                                   2   
    ===================================================================
    Connection Statistics
    ===================================================================
       Sort Records                                   3260 
       Sort Sets                                      2  
    =================================================================== 
    DBCC Info    
    ===================================================================
       DBCC Work units Dispatched                     197  
       DBCC Work units Completed                      197  
       DBCC Buffer Quota                              255  
       DBCC Per-Thread Buffer Quota                   255  
       Max Blockmap ID found                          200  
       Max Transaction ID found                       404
    ```

    ```

    ```

    > ### Note:  
    > The report may indicate leaked space. Leaked space is a block that is allocated according to the database free list \(an internal allocation map\), but DBCC finds that the block is not part of any database object.


