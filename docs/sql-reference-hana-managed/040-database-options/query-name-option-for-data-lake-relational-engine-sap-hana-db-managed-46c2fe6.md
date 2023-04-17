<!-- loio46c2fe6f4e30441c982519451fa6a6bf -->

# QUERY\_NAME Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Gives a name to an executed query in its query plan.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio46c2fe6f4e30441c982519451fa6a6bf__section_tsb_5bt_lrb"/>

## Syntax

```
QUERY_NAME = <string_expression>
```



<a name="loio46c2fe6f4e30441c982519451fa6a6bf__section_p5l_5bt_lrb"/>

## Allowed Values

Quote-delimited string of up to 80 characters.



<a name="loio46c2fe6f4e30441c982519451fa6a6bf__section_x2v_5bt_lrb"/>

## Default

' ' \(the empty string\)



<a name="loio46c2fe6f4e30441c982519451fa6a6bf__section_hqs_ksb_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio46c2fe6f4e30441c982519451fa6a6bf__section_zbt_vbt_lrb"/>

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

No



</td>
</tr>
</table>



<a name="loio46c2fe6f4e30441c982519451fa6a6bf__section_h4g_wbt_lrb"/>

## Remarks

You can assign the QUERY\_NAME option any quote-delimited string value, up to 80 characters. For example:

```
set temporary option Query_Name = 'my third query'
```

When this option is set, query plans that are sent to the `.iqmsg` file or `.html` file include a line near the top of the plan that looks like:

```
Query_Name:  'my third query'
```

If you set the option to a different value before each query in a script, it is much easier to identify the correct query plan for a particular query. The query name is also added to the file name for HTML query plans. This option has no other effect on the query.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[QUERY_NAME Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a64cbcec84f21015a49bf2d389632729.html "Gives a name to an executed query in its query plan.") :arrow_upper_right:

