<!-- loioabcd7031a1414519a71684edac0debc6 -->

# SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database

Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.



> ### Caution:  
> This procedure is only for setting options temporarily in a relational container. To set options permanently, use the data lake Relational Engine SET OPTION statement. See [SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md).



```
CALL <relational_container_schema_name>.SET_TEMPORARY_OPTION( '<option_name>', '<option_value>' )
```



<a name="loioabcd7031a1414519a71684edac0debc6__section_i2n_cmz_gxb"/>

## Parameter


<dl>
<dt><b>

*<option\_name\>*

</b></dt>
<dd>

The name of the option to set as temporary, with no owner prefix.



</dd><dt><b>

*<option\_value\>*

</b></dt>
<dd>

The value to set the option to. The value is treated as a string, even when a number is entered, and must be enclosed in single quotation marks. To reset the option to its default value, enter NULL \(without quotation marks\) or leave out the second argument. For example, the following syntax are equivalent to reset the option to the default value.

```
CALL SYSHDL_CONTAINER1.SET_TEMPORARY_OPTION('DATE_FIRST_DAY_OF_WEEK', NULL);
CALL SYSHDL_CONTAINER1.SET_TEMPORARY_OPTION('DATE_FIRST_DAY_OF_WEEK');
```



</dd>
</dl>



<a name="loioabcd7031a1414519a71684edac0debc6__section_zhc_rnx_cjb"/>

## Description

Sets a database option temporarily for the duration of the current connection.



<a name="loioabcd7031a1414519a71684edac0debc6__section_xlt_rnx_cjb"/>

## Privileges

You are a member of the container administrator role, SYSHDL\_*<relational\_container\_name\>*\_ROLE.



<a name="loioabcd7031a1414519a71684edac0debc6__section_f5l_5nx_cjb"/>

## Example

The following example temporarily sets the DATE\_FIRST\_DAY\_OF\_WEEK option to Monday.

```
CALL SYSHDL_CONTAINER1.SET_TEMPORARY_OPTION('DATE_FIRST_DAY_OF_WEEK', '1');
```

The following two examples unset the DATE\_FIRST\_DAY\_OF\_WEEK option back to the default value of 0 \(Sunday\).

```
CALL SYSHDL_CONTAINER1.SET_TEMPORARY_OPTION('DATE_FIRST_DAY_OF_WEEK', NULL);
```

```
CALL SYSHDL_CONTAINER1.SET_TEMPORARY_OPTION('DATE_FIRST_DAY_OF_WEEK');
```

**Related Information**  


[Alphabetical List of Settable Database Options in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../040-database-options/alphabetical-list-of-settable-database-options-in-data-lake-relational-engine-sap-hana-db-a7f7159.md "Settable database options let you configure database behavior.")

