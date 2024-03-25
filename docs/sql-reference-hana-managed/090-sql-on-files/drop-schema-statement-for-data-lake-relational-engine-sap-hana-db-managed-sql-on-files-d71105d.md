<!-- loiod71105d49064495ca6a2be5cf34348d7 -->

# DROP SCHEMA Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]

Drop a remote schema, which is a collection of remote tables, in a SQL on Files external catalog.



<a name="loiod71105d49064495ca6a2be5cf34348d7__section_inj_b3b_nqb"/>

## Usage

-   This topic is limited to SQL on Files use cases.

-   This data lake Relational Engine \(SAP HANA DB-Managed\) SQL on Files SQL statement can be used as follows:

    -   Connected to SAP HANA database as a SAP HANA database user..
    -   Using the REMOTE\_EXECUTE procedure. See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](../030-sql-statements/remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).





## Syntax

```
DROP SCHEMA <remote-schema-name> [ CASCADE ] IN FILES_SERVICE;
```



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



## Remarks

The `DROP SCHEMA` SQL on Files statement drops the schema with the given name. If CASCADE is not specified, all tables in this schema must be dropped before the schema is dropped.



<a name="loiod71105d49064495ca6a2be5cf34348d7__section_zy1_g4b_nqb"/>

## Privileges

To use REMOTE\_EXECUTE requires one of the following:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



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


[REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](../030-sql-statements/remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md "To run data lake Relational Engine SQL statements using the SAP HANA database REMOTE_EXECUTE or REMOTE_EXECUTE_DDL procedure, you embed the SQL syntax within the procedure.")

[DROP SCHEMA Statement for Data Lake Relational Engine \[SQL on Files\]](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/9b97bf4f782643a7b197762f36623071.html "Drop a remote schema, which is a collection of remote tables, in a SQL on Files external catalog.") :arrow_upper_right:

