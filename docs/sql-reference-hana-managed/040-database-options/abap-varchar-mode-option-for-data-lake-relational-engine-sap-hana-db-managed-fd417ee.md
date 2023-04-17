<!-- loiofd417eec6ec840f291da03d66ab3c773 -->

# ABAP\_VARCHAR\_MODE Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls whether a SQL string or expression that contains a single space is considered the same as an empty string.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loiofd417eec6ec840f291da03d66ab3c773__section_vll_yg2_crb"/>

## Syntax

```
ABAP_VARCHAR_MODE = { ON | OFF }
```



<a name="loiofd417eec6ec840f291da03d66ab3c773__section_csy_yg2_crb"/>

## Allowed Values

ON, OFF



<a name="loiofd417eec6ec840f291da03d66ab3c773__section_irk_zg2_crb"/>

## Default

OFF



<a name="loiofd417eec6ec840f291da03d66ab3c773__section_m53_35v_cxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loiofd417eec6ec840f291da03d66ab3c773__section_b5b_knb_dxb"/>

## Scope


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

PUBLIC Role



</th>
<th valign="top">

For Current User



</th>
<th valign="top">

For Other Users



</th>
</tr>
<tr>
<td valign="top">

Allowed to set permanently?



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes \(current connection only\)



</td>
<td valign="top">

Yes



</td>
</tr>
</table>



<a name="loiofd417eec6ec840f291da03d66ab3c773__section_kzp_ch2_crb"/>

## Remarks

In ABAP VARCHAR mode, a single space and an empty string are considered the same and concatenated strings are reduced from a single space to an empty string.

To insert a single space when ABAP VARCHAR mode is turned on, use CHAR\(32\) to insert the single space instead of ' '.

Because using ABAP VARCHAR mode causes semantic differences when you insert data into a table, turning on this option affects the LIKE and EQUALITY predicates.

**Related Information**  


[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[ABAP_VARCHAR_MODE Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/62acec57c05b463ca9add28e6bf066e2.html "Controls whether a SQL string or expression that contains a single space is considered the same as an empty string.") :arrow_upper_right:

