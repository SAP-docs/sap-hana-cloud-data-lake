<!-- loio2d1730263f004bf5a3728cc25edc5ea1 -->

# DATE\_ORDER Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls the interpretation of date formats.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio2d1730263f004bf5a3728cc25edc5ea1__section_vd1_qd4_hrb"/>

## Syntax

```
DATE_ORDER = { MDY | YMD | DMY }
```



<a name="loio2d1730263f004bf5a3728cc25edc5ea1__section_qwl_qd4_hrb"/>

## Allowed Values

'MDY', 'YMD', or 'DMY'



<a name="loio2d1730263f004bf5a3728cc25edc5ea1__section_odx_qd4_hrb"/>

## Default

'YMD'. This corresponds to ISO date format specifications.

'MDY' for Open Client and JDBC connections



<a name="loio2d1730263f004bf5a3728cc25edc5ea1__section_bx1_1cw_cxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio2d1730263f004bf5a3728cc25edc5ea1__section_ph5_hmb_dxb"/>

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



<a name="loio2d1730263f004bf5a3728cc25edc5ea1__section_gn3_5d4_hrb"/>

## Remarks

DATE\_ORDER is used to determine whether 10/11/12 is Oct 11 1912, Nov 12 1910, or Nov 10 1912. The option can have the value 'MDY', 'YMD', or 'DMY'.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[DATE_ORDER Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a632876d84f21015855da65181715d7a.html "Controls the interpretation of date formats.") :arrow_upper_right:

