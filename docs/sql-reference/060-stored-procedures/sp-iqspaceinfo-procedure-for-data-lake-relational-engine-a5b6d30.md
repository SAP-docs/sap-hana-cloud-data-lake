<!-- loioa5b6d30884f21015b460b72ef2bc8109 -->

# sp\_iqspaceinfo Procedure for Data Lake Relational Engine

Displays the number of blocks\(objects\) used by each object in the current database and the name of the dbspace in which the object is located.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqspaceinfo ['main | [table <table-name> | index <index-name>] [...] ']
```



<a name="loioa5b6d30884f21015b460b72ef2bc8109__iq_refbb_1759"/>

## Parameters


<dl>
<dt><b>

*<table-name\>*

</b></dt>
<dd>

The name of the table.



</dd><dt><b>

*<index-name\>*

</b></dt>
<dd>

The name of the index.



</dd>
</dl>



<a name="loioa5b6d30884f21015b460b72ef2bc8109__iq_refbb_1761"/>

## Remarks

For the current database, displays the object name, number of blocks\(or objects, in instances using cloud dbspaces\) used by each object, and the name of the dbspace. sp\_iqspaceinfo requires no parameters.

The information returned by sp\_iqspaceinfo is helpful in managing dbspaces.

If run on a multiplex database, the default parameter is main, which returns the size of the shared data lake Relational Engine store.

If you supply no parameter, you need to have at least one user-created object, such as a table, to receive results.



<a name="loioa5b6d30884f21015b460b72ef2bc8109__iq_refbb_1760"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure along with the MANAGE ANY DBSPACE system privilege.



## Side Effects

None



<a name="loioa5b6d30884f21015b460b72ef2bc8109__iq_refbb_1762"/>

## Example

This output is from the sp\_iqspaceinfo stored procedure run on the iqdemo database. Output for some tables and indexes are removed from this example:

```
             Name                            NBlocks    dbspace_name
```

```
Contacts                                      19       IQ_SYSTEM_MAIN 
SalesOrderItems.DBA.ASIQ_IDX_T205_C5_FP       56       IQ_SYSTEM_MAIN 
Contacts.DBA.ASIQ_IDX_T206_C10_FP             55       IQ_SYSTEM_MAIN 
Contacts.DBA.ASIQ_IDX_T206_C1_FP              61       IQ_SYSTEM_MAIN 
...
Contacts.DBA.ASIQ_IDX_T206_C9_FP              55       IQ_SYSTEM_MAIN 
Contacts.DBA.ASIQ_IDX_T206_I11_HG             19       IQ_SYSTEM_MAIN 
Customers                                     20       IQ_SYSTEM_MAIN 
Customers.DBA.ASIQ_IDX_T207_C1_FP             61       IQ_SYSTEM_MAIN 
Customers.DBA.ASIQ_IDX_T207_C2_FP             55       IQ_SYSTEM_MAIN 
...
Customers.DBA.ASIQ_IDX_T207_I10_HG            19       IQ_SYSTEM_MAIN 
...
```

**Related Information**  


[sp\_iqindexinfo Procedure for Data Lake Relational Engine](sp-iqindexinfo-procedure-for-data-lake-relational-engine-a5ac909.md "Displays the number of blocks (objects) used per index per main dbspace for a given object. If the object resides on several dbspaces, sp_iqindexinfo returns the space used in all dbspaces, as shown in the example.")

[sp\_iqdbspace Procedure for Data Lake Relational Engine](sp-iqdbspace-procedure-for-data-lake-relational-engine-a5a34b5.md "Displays detailed information about each data lake Relational Engine dbspace.")

[sp\_iqdbspaceinfo Procedure for Data Lake Relational Engine](sp-iqdbspaceinfo-procedure-for-data-lake-relational-engine-a5a3ca6.md "Displays the size of each object and subobject used in the specified table.")

[Cloud Dbspaces](https://help.sap.com/viewer/a896c6a184f21015b5bcf4c7a967df07/2023_2_QRC/en-US/493eb818429e4996b3da4153192a9efa.html "Cloud dbspace is a new offering where the database engine stores a user dbspace in object storage solutions such as Microsoft Azure Blob Storage, AWS Simple Storage Service (S3), or Google Cloud Storage. In a cloud dbspace, database pages are physically stored as objects as opposed to regular file system blocks.") :arrow_upper_right:

