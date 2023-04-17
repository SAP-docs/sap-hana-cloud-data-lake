<!-- loioe245892799f64df68ade16f24f1ddfb0 -->

# LOAD\_PREFETCH\_LOOKAHEAD Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Specify a higher prefetch lookahead value or lets the system set automatically based on the IO latency to improve performance with the LOAD statement.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loioe245892799f64df68ade16f24f1ddfb0__section_o1y_kbg_htb"/>

## Syntax

```
LOAD_PREFETCH_LOOKAHEAD = <value>
```



<a name="loioe245892799f64df68ade16f24f1ddfb0__section_mgb_mbg_htb"/>

## Allowed Values


<table>
<tr>
<th valign="top">

Value



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

\-1



</td>
<td valign="top">

Disables adaptive prefetching. The original prefetch approach where the lookahead value is 1 is used.



</td>
</tr>
<tr>
<td valign="top">

0



</td>
<td valign="top">

Enables adaptive prefetching.



</td>
</tr>
<tr>
<td valign="top">

1 to 15



</td>
<td valign="top">

Specifies the lookahead value to use for adaptive prefetching to a maximum of 15.



</td>
</tr>
</table>



<a name="loioe245892799f64df68ade16f24f1ddfb0__section_otr_mbg_htb"/>

## Default

0



<a name="loioe245892799f64df68ade16f24f1ddfb0__section_cnd_2cw_cxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loioe245892799f64df68ade16f24f1ddfb0__section_nkb_wlb_dxb"/>

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

**Related Information**  


[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[LOAD_PREFETCH_LOOKAHEAD Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/912d8f5b53a54ea5ad4c23fbf5198644.html "Specify a higher prefetch lookahead value or lets the system set automatically based on the IO latency to improve performance with the LOAD statement.") :arrow_upper_right:

