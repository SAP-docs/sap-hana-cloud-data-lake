<!-- loiof81d073adf494841b1f7ece9ed0e7266 -->

# DROP \(Remote\) TABLE Statement for Data Lake Relational Engine \[SQL on Files\]

Drop a remote table from a SQL on Files external catalog.



<a name="loiof81d073adf494841b1f7ece9ed0e7266__section_fry_b3b_nqb"/>

## Usage

-   This topic is limited to SQL on Files use cases.
-   This SQL on Files SQL statement can be used when connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loiof81d073adf494841b1f7ece9ed0e7266__DT_syntax"/>

## Syntax

```
DROP TABLE <remote-schema-name>.<remote-table-name> IN FILES_SERVICE;
```



<a name="loiof81d073adf494841b1f7ece9ed0e7266__DT_parameters"/>

## Parameters


<dl>
<dt><b>

*<remote-schema-name\>*

</b></dt>
<dd>

The schema of the table. *<remote-schema-name\>* must be provided.



</dd><dt><b>

*<remote-table-name\>*

</b></dt>
<dd>

The name of the table to be deleted.



</dd>
</dl>



## Privileges

You have been granted the HDL\_FILES\_SERVICE\_ADMIN role or the DROP TABLE FILES SERVICE privilege.



<a name="loiof81d073adf494841b1f7ece9ed0e7266__DT_example"/>

## Examples

The following statement drops the table `ExternalTable1`:

```
DROP TABLE ExternalSchema1.ExternalTable1 IN FILES_SERVICE;
```

**Related Information**  


[ALTER \(Remote\) TABLE Statement with REFRESH for Data Lake Relational Engine \[SQL on Files\]](alter-remote-table-statement-with-refresh-for-data-lake-relational-engine-sql-on-files-ae56450.md "Alter the refresh mode of a table.")

[CREATE \(Remote\) TABLE Statement for Data Lake Relational Engine \[SQL on Files\]](create-remote-table-statement-for-data-lake-relational-engine-sql-on-files-beffc07.md "Create a remote table managed by SQL on Files.")

[REFRESH \(Remote\) TABLE Statement for Data Lake Relational Engine \[SQL on Files\]](refresh-remote-table-statement-for-data-lake-relational-engine-sql-on-files-e275657.md "Update the current list of data source files for a SQL on Files remote table by performing a directory scan on all current data sources attached to this remote table.")

[DROP (Remote) TABLE Statement for Data Lake Relational Engine (SAP HANA DB-Managed) \[SQL on Files\]](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/ca1e55df6c6f4e0aa381832e5504a4b9.html "Drop a remote table from a SQL on Files external catalog.") :arrow_upper_right:

