<!-- loioaf3fb5b713f34db2aaa8efbf0c2a9e45 -->

# CREATE SCHEMA Statement for Data Lake Relational Engine \[SQL on Files\]

Create a schema, which is a collection of tables, managed by SQL on Files.



<a name="loioaf3fb5b713f34db2aaa8efbf0c2a9e45__section_fry_b3b_nqb"/>

## Usage

-   This topic is limited to SQL on Files use cases.
-   This SQL on Files SQL statement can be used when connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioaf3fb5b713f34db2aaa8efbf0c2a9e45__CS_syntax"/>

## Syntax

```
CREATE SCHEMA <remote-schema-name> IN FILES_SERVICE;
```



<a name="loioaf3fb5b713f34db2aaa8efbf0c2a9e45__CS_parameters"/>

## Parameters


<dl>
<dt><b>

*<remote-schema-name\>*

</b></dt>
<dd>

The name of the new schema. If the schema already exists in SQL on Files, an error is returned.



</dd>
</dl>



<a name="loioaf3fb5b713f34db2aaa8efbf0c2a9e45__CS_remarks"/>

## Remarks

The SQL on Files external catalog stores the remote schema definition. This remote schema will have a collection of remote tables, and each remote table must belong to an existing remote schema.



## Privileges

You have been granted the HDL\_FILES\_SERVICE\_ADMIN role or the CREATE SCHEMA FILES SERVICE privilege.



<a name="loioaf3fb5b713f34db2aaa8efbf0c2a9e45__CS_example"/>

## Examples

The following statement creates the schema `Factory`:

```
CREATE SCHEMA Factory IN FILES_SERVICE;
```

**Related Information**  


[CREATE SCHEMA Statement for Data Lake Relational Engine (SAP HANA DB-Managed) \[SQL on Files\]](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/5cd793c72fd34f4bb337698fa11ea3d0.html "Create a schema, which is a collection of tables, managed by SQL on Files.") :arrow_upper_right:

