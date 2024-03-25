<!-- loiof263dc28f1b949218ef7ba6c4b0f82dc -->

# SYSCOLUMNS System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYSCOLUMNS view describes one column of each table and view in the catalog.



<a name="loiof263dc28f1b949218ef7ba6c4b0f82dc__section_mmm_ys1_4yb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user, and using SAP HANA database REMOTE\_EXECUTE\_QUERY.




The tables and columns that make up this view are provided in the SQL statement below. To learn more about a particular table or column, use the links provided beneath the view definition.

```
ALTER VIEW "SYS"."SYSCOLUMNS"( creator,cname,tname,coltype,nulls,length,
  syslength,in_primary_key,colno,default_value,
  column_kind,remarks ) 
  as select u.user_name,col.column_name,tab.table_name,dom.domain_name,
    col.nulls,col.width,col.scale,if ixcol.sequence is null then 'N' else 'Y' endif,col.column_id,
    col."default",col.column_type,rmk.remarks
    from SYS.SYSTABCOL as col
      left outer join SYS.ISYSIDXCOL as ixcol on(col.table_id = ixcol.table_id and col.column_id = ixcol.column_id and ixcol.index_id = 0)
      join SYS.ISYSTAB as tab on(tab.table_id = col.table_id)
      join SYS.ISYSDOMAIN as dom on(dom.domain_id = col.domain_id)
      join SYS.ISYSUSER as u on u.user_id = tab.creator
      left outer join SYS.ISYSREMARK as rmk on(col.object_id = rmk.object_id);
```



<a name="loiof263dc28f1b949218ef7ba6c4b0f82dc__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSCOLUMNS Consolidated View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/3be74eee6c5f1014a3def3d1f8953400.html "Each row in the SYSCOLUMNS view describes one column of each table and view in the catalog.") :arrow_upper_right:

