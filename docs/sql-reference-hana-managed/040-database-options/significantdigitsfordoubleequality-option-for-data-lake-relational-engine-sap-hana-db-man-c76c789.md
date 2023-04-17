<!-- loioc76c789fc5c64cc8bcdbb0a22e3ad765 -->

# SIGNIFICANTDIGITSFORDOUBLEEQUALITY Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Specifies the number of significant digits to the right of the decimal in exponential notation that are used in equality tests between two complex arithmetic expressions.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loioc76c789fc5c64cc8bcdbb0a22e3ad765__section_erj_vrz_lrb"/>

## Syntax

```
SIGNIFICANTDIGITSFORDOUBLEEQUALITY = <number_expression>
```



<a name="loioc76c789fc5c64cc8bcdbb0a22e3ad765__section_snx_vrz_lrb"/>

## Allowed Values

0 to 15



<a name="loioc76c789fc5c64cc8bcdbb0a22e3ad765__section_axk_wrz_lrb"/>

## Default

0



<a name="loioc76c789fc5c64cc8bcdbb0a22e3ad765__section_q2h_bvb_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loioc76c789fc5c64cc8bcdbb0a22e3ad765__section_sp1_xrz_lrb"/>

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



<a name="loioc76c789fc5c64cc8bcdbb0a22e3ad765__section_gqz_xrz_lrb"/>

## Remarks

Doubles are stored in binary \(base 2\) instead of decimal \(base 10\); this means that this setting gives the approximate number of significant decimal digits used. If set to 0, all digits are used.

For example, when SIGNIFICANTDIGITSFORDOUBLEEQUALITY is set to 12, these numbers compare as equal; when set to 13, they do not:

-   1.23456789012345
-   1.23456789012389

SIGNIFICANTDIGITSFORDOUBLEEQUALITY affects equality tests between two complex arithmetic expressions, not those done by the indexes.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[SIGNIFICANTDIGITSFORDOUBLEEQUALITY Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a6548b1c84f210159d55cfd18f663415.html "Specifies the number of significant digits to the right of the decimal in exponential notation that are used in equality tests between two complex arithmetic expressions.") :arrow_upper_right:

