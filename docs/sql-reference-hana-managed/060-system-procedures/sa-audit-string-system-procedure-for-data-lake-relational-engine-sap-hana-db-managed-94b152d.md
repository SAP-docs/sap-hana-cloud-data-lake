<!-- loio94b152d9c67043c2828e4f3de384856b -->

# sa\_audit\_string System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Adds a string to auditing data.



<a name="loio94b152d9c67043c2828e4f3de384856b__section_dh4_3db_1yb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

> ### Restriction:  
> This syntax cannot be run when connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_QUERY.



```
sa_audit_string( <string> )
```



<a name="loio94b152d9c67043c2828e4f3de384856b__section_ns5_ct4_rrc"/>

## Parameters


<dl>
<dt><b>

*<string\>* 

</b></dt>
<dd>

The VARCHAR\(128\) string of characters to add.



</dd>
</dl>



<a name="loio94b152d9c67043c2828e4f3de384856b__section_m3f_fnf_zyb"/>

## Result Set

None.



<a name="loio94b152d9c67043c2828e4f3de384856b__section_a44_dt4_rrd"/>

## Remarks

If auditing is turned on, then this system procedure adds a comment to the auditing information. The string can be a maximum of 128 characters.



<a name="loio94b152d9c67043c2828e4f3de384856b__section_sxm_n1b_1yb"/>

## Privileges



### 

Require all of the following:

-   EXECUTE object-level privilege on this procedure
-   MANAGE AUDITING system privilege



<a name="loio94b152d9c67043c2828e4f3de384856b__section_rxd_2t4_rre"/>

## Side Effects

None.



<a name="loio94b152d9c67043c2828e4f3de384856b__section_rxd_2t4_rrf"/>

## Examples

This example adds text to the audit string.

```
CALL sa_audit_string ('Auditing test start');
```

**Related Information**  


[sa_audit_string System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/3be55c396c5f1014a724eb3c15a43d25.html "Adds a string to auditing data.") :arrow_upper_right:

