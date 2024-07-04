<!-- loio2918c50e87e2453187cd8c1e9d043c64 -->

# DROP PSE Statement for Data Lake Relational Engine

Removes a personal security environment \(PSE\) from the database.



<a name="loio2918c50e87e2453187cd8c1e9d043c64__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
PSE <pse-name> [ CASCADE ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio2918c50e87e2453187cd8c1e9d043c64__drop_pse_param1"/>

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



<a name="loio2918c50e87e2453187cd8c1e9d043c64__drop_pse_remarks1"/>

## Remarks

None



<a name="loio2918c50e87e2453187cd8c1e9d043c64__drop_pse_priv1"/>

## Privileges



### 

You own the PSE.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loio2918c50e87e2453187cd8c1e9d043c64__drop_pse_side_efects1"/>

## Side Effects

-   Automatic commit.



<a name="loio2918c50e87e2453187cd8c1e9d043c64__examples1"/>

## Examples

This example drops the PSE mypse1, regardless of whether there are credentials or certificates that reference the PSE.

```
DROP PSE mypse1 CASCADE;
```

**Related Information**  


[CREATE PSE Statement for Data Lake Relational Engine](create-pse-statement-for-data-lake-relational-engine-cda6e32.md "Create a personal security environment (PSE).")

[ALTER PSE Statement for Data Lake Relational Engine](alter-pse-statement-for-data-lake-relational-engine-53742a2.md "Modifies an existing personal security environment (PSE).")

[DROP PSE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/daf65f665de04d3e9ae628fc2cc97cfe.html "Removes a personal security environment (PSE) from the database.") :arrow_upper_right:

