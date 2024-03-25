<!-- loiobc673dbe10aa4a5da1d6b1c3a1d7e7ce -->

# CREATE PSE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Create a personal security environment \(PSE\).



<a name="loiobc673dbe10aa4a5da1d6b1c3a1d7e7ce__section_lv2_3cg_2zb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
CREATE PSE <pse-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiobc673dbe10aa4a5da1d6b1c3a1d7e7ce__section_q41_nbb_fzb"/>

## Parameters


<dl>
<dt><b>

*<pse-name\>*

</b></dt>
<dd>

Specifies a unique name for the PSE.

```
<pse-name> ::= <simple_identifier>
```



</dd>
</dl>



<a name="loiobc673dbe10aa4a5da1d6b1c3a1d7e7ce__section_j4p_nbb_fzb"/>

## Remarks

PSEs are used for trust validation in data lake Relational Engine. They are sometimes referred to as certificate collections.



<a name="loiobc673dbe10aa4a5da1d6b1c3a1d7e7ce__section_kmj_sbb_fzb"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user.:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd>
</dl>



<a name="loiobc673dbe10aa4a5da1d6b1c3a1d7e7ce__section_iyz_sbb_fzb"/>

## Side Effects

Automatic commit



<a name="loiobc673dbe10aa4a5da1d6b1c3a1d7e7ce__section_i5k_tbb_fzb"/>

## Examples

This example creates a PSE named mypse1.

```
CREATE PSE mypse1;
```

**Related Information**  


[ALTER PSE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-pse-statement-for-data-lake-relational-engine-sap-hana-db-managed-056ee2c.md "Modifies an existing personal security environment (PSE).")

[DROP PSE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-pse-statement-for-data-lake-relational-engine-sap-hana-db-managed-daf65f6.md "Removes a personal security environment (PSE) from the database.")

[SYSPSE System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../070-system-views/syspse-system-view-for-data-lake-relational-engine-sap-hana-db-managed-0211aea.md "Provides information about personal security environments (PSE).")

[CREATE PSE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/cda6e32786854f6c9f9cc1869c6ddca1.html "Create a personal security environment (PSE).") :arrow_upper_right:

