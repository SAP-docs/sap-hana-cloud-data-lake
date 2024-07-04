<!-- loiodaf65f665de04d3e9ae628fc2cc97cfe -->

# DROP PSE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes a personal security environment \(PSE\) from the database.



<a name="loiodaf65f665de04d3e9ae628fc2cc97cfe__section_egm_jff_2zb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
PSE <pse-name> [ CASCADE ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiodaf65f665de04d3e9ae628fc2cc97cfe__section_alb_4ff_2zb"/>

## Parameters


<dl>
<dt><b>

*<pse-name\>*

</b></dt>
<dd>

Specifies the PSE name being dropped.



</dd><dt><b>

CASCADE

</b></dt>
<dd>

Removes all mappings that reference the PSE. If not specified, then the drop fails if there are any certificates or credentials that reference the PSE.



</dd>
</dl>



<a name="loiodaf65f665de04d3e9ae628fc2cc97cfe__section_wt5_4ff_2zb"/>

## Remarks

None



<a name="loiodaf65f665de04d3e9ae628fc2cc97cfe__section_ldn_pff_2zb"/>

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



<a name="loiodaf65f665de04d3e9ae628fc2cc97cfe__section_y3t_rff_2zb"/>

## Side Effects

-   Automatic commit.



<a name="loiodaf65f665de04d3e9ae628fc2cc97cfe__section_d5k_sff_2zb"/>

## Examples

This example drops the PSE mypse1, regardless of whether there are credentials or certificates that reference the PSE.

```
DROP PSE mypse1 CASCADE;
```

**Related Information**  


[CREATE PSE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-pse-statement-for-data-lake-relational-engine-sap-hana-db-managed-bc673db.md "Create a personal security environment (PSE).")

[DROP PSE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-pse-statement-for-data-lake-relational-engine-sap-hana-db-managed-daf65f6.md "Removes a personal security environment (PSE) from the database.")

[DROP PSE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/2918c50e87e2453187cd8c1e9d043c64.html "Removes a personal security environment (PSE) from the database.") :arrow_upper_right:

