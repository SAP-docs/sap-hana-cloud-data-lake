<!-- loiocda6e32786854f6c9f9cc1869c6ddca1 -->

# CREATE PSE Statement for Data Lake Relational Engine

Create a personal security environment \(PSE\).



<a name="loiocda6e32786854f6c9f9cc1869c6ddca1__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE PSE <pse-name>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiocda6e32786854f6c9f9cc1869c6ddca1__create_pse_param1"/>

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



<a name="loiocda6e32786854f6c9f9cc1869c6ddca1__create_pse_remarks1"/>

## Remarks

PSEs are used for trust validation in data lake Relational Engine. They are sometimes referred to as certificate collections.



<a name="loiocda6e32786854f6c9f9cc1869c6ddca1__create_pse_priv1"/>

## Privileges



### 

Requires the MANAGE TRUST system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loiocda6e32786854f6c9f9cc1869c6ddca1__create_pse_side_effect1"/>

## Side Effects

Automatic commit



<a name="loiocda6e32786854f6c9f9cc1869c6ddca1__create_pse_examples1"/>

## Examples

This example creates a PSE named mypse1.

```
CREATE PSE mypse1;
```

**Related Information**  


[ALTER PSE Statement for Data Lake Relational Engine](alter-pse-statement-for-data-lake-relational-engine-53742a2.md "Modifies an existing personal security environment (PSE).")

[DROP PSE Statement for Data Lake Relational Engine](drop-pse-statement-for-data-lake-relational-engine-2918c50.md "Removes a personal security environment (PSE) from the database.")

[SYSPSE System View for Data Lake Relational Engine](../070-system-and-monitoring-views/syspse-system-view-for-data-lake-relational-engine-e009d26.md "Provides information about personal security environments (PSE).")

[CREATE PSE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/bc673dbe10aa4a5da1d6b1c3a1d7e7ce.html "Create a personal security environment (PSE).") :arrow_upper_right:

