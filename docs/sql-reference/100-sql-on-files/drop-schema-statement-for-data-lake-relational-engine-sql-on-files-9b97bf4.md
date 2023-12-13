<!-- loio9b97bf4f782643a7b197762f36623071 -->

# DROP SCHEMA Statement for Data Lake Relational Engine \[SQL on Files\]

Drop a remote schema, which is a collection of remote tables, in a SQL on Files external catalog.



<a name="loio9b97bf4f782643a7b197762f36623071__section_fry_b3b_nqb"/>

## Usage

-   This topic is limited to SQL on Files use cases.
-   This SQL on Files SQL statement can be used when connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio9b97bf4f782643a7b197762f36623071__DS_syntax"/>

## Syntax

```
DROP SCHEMA <remote-schema-name> [ CASCADE ] IN FILES_SERVICE;
```



<a name="loio9b97bf4f782643a7b197762f36623071__DS_parameters"/>

## Parameters


<dl>
<dt><b>

*<remote-schema-name\>*

</b></dt>
<dd>

The name of the schema to be deleted.



</dd><dt><b>

CASCADE

</b></dt>
<dd>

The remote tables in the remote schema are dropped before the schema itself is dropped.



</dd>
</dl>



<a name="loio9b97bf4f782643a7b197762f36623071__DS_remarks"/>

## Remarks

The `DROP SCHEMA` SQL on Files statement drops the schema with the given name. If CASCADE is not specified, all tables in this schema must be dropped before the schema is dropped.



## Privileges

You have been granted the HDL\_FILES\_SERVICE\_ADMIN role or the DROP SCHEMA FILES SERVICE privilege.



<a name="loio9b97bf4f782643a7b197762f36623071__DS_example"/>

## Examples

The following example drops the schema `Factory`:

```
DROP SCHEMA Factory IN FILES_SERVICE;
```

The following example drops all tables from the schema `Factory` and then drops the schema `Factory` itself:

```
DROP SCHEMA Factory CASCADE IN FILES_SERVICE;
```

**Related Information**  


[DROP SCHEMA Statement for Data Lake Relational Engine (SAP HANA DB-Managed) \[SQL on Files\]](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/d71105d49064495ca6a2be5cf34348d7.html "Drop a remote schema, which is a collection of remote tables, in a SQL on Files external catalog.") :arrow_upper_right:

