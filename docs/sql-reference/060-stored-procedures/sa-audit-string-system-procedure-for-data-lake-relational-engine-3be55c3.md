<!-- loio3be55c396c5f1014a724eb3c15a43d25 -->

# sa\_audit\_string System Procedure for Data Lake Relational Engine

Adds a string to auditing data.



<a name="loio3be55c396c5f1014a724eb3c15a43d25__section_rpg_3dw_f4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_audit_string( <string> )
```



<a name="loio3be55c396c5f1014a724eb3c15a43d25__sa_audit_string_param1"/>

## Parameters


<dl>
<dt><b>

*<string\>* 

</b></dt>
<dd>

The VARCHAR\(128\) string of characters to add.



</dd>
</dl>



<a name="loio3be55c396c5f1014a724eb3c15a43d25__sa_audit_string_result1"/>

## Result Set

None.



<a name="loio3be55c396c5f1014a724eb3c15a43d25__sa_audit_string_remarks1"/>

## Remarks

If auditing is turned on, then this system procedure adds a comment to the auditing information. The string can be a maximum of 128 characters.



<a name="loio3be55c396c5f1014a724eb3c15a43d25__sa_audit_string_priv1"/>

## Privileges



### 

Require all of the following:

-   EXECUTE object-level privilege on this procedure
-   MANAGE AUDITING system privilege



<a name="loio3be55c396c5f1014a724eb3c15a43d25__sa_audit_string_sideefects1"/>

## Side Effects

None.



<a name="loio3be55c396c5f1014a724eb3c15a43d25__sa_audit_string_example"/>

## Examples

This example adds text to the audit string.

```
CALL sa_audit_string ('Auditing test start');
```

**Related Information**  


[sa_dependent_views System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/47783e3af31b4f27a28b41ad534f8332.html "Returns the list of all dependent views for a given table or view.") :arrow_upper_right:

[sa_audit_string System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/94b152d9c67043c2828e4f3de384856b.html "Adds a string to auditing data.") :arrow_upper_right:

