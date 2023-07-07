<!-- loio94b152d9c67043c2828e4f3de384856b -->

# sa\_audit\_string System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Adds a string to auditing data.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Running Procedures](remote-execute-usage-examples-for-running-procedures-3e7f86d.md) for more information.



```
dbo.sa_audit_string( <string> )
```



<a name="loio94b152d9c67043c2828e4f3de384856b__section_ns5_ct4_rrb"/>

## Parameters


<dl>
<dt><b>

 *<string\>* 

</b></dt>
<dd>

The VARCHAR\(128\) string of characters to add.



</dd>
</dl>



<a name="loio94b152d9c67043c2828e4f3de384856b__section_a44_dt4_rrb"/>

## Remarks

If auditing is turned on, then this system procedure adds a comment to the auditing information. The string can be a maximum of 128 characters.



<a name="loio94b152d9c67043c2828e4f3de384856b__section_ivx_djx_s3b"/>

## Privileges

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio94b152d9c67043c2828e4f3de384856b__section_rxd_2t4_rrb"/>

## Side Effects

None

**Related Information**  


[sa_audit_string System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/3be55c396c5f1014a724eb3c15a43d25.html "Adds a string to auditing data.") :arrow_upper_right:

