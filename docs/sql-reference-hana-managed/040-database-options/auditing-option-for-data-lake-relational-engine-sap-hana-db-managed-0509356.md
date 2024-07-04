<!-- loio05093562ca224fc2a9bbd3d9d587362c -->

# AUDITING Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Enables and disables auditing in the database.



<a name="loio05093562ca224fc2a9bbd3d9d587362c__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio05093562ca224fc2a9bbd3d9d587362c__section_h5n_ppy_brb"/>

## Syntax

```
AUDITING = { ON | OFF };
```



<a name="loio05093562ca224fc2a9bbd3d9d587362c__section_op2_23y_brb"/>

## Allowed Values

ON, OFF



<a name="loio05093562ca224fc2a9bbd3d9d587362c__section_l5r_23y_brb"/>

## Default

OFF



<a name="loio05093562ca224fc2a9bbd3d9d587362c__section_f2n_1xv_cxb"/>

## Privileges

Privilege Category: SECURITY



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user:

</b></dt>
<dd>

-   To set a database option permanently, use REMOTE\_EXECUTE.

    Requires one of:

    -   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
    -   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

    -   See [REMOTE\_EXECUTE Guidance and Examples for Setting Permanent Database Options](remote-execute-guidance-and-examples-for-setting-permanent-database-options-0023bea.md).





</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

Requires all of:

-   MANAGE AUDITING system privilege
-   SET ANY CUSTOMER SECURITY OPTION system privilege



</dd>
</dl>



<a name="loio05093562ca224fc2a9bbd3d9d587362c__section_u15_zmb_dxb"/>

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

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
</table>



<a name="loio05093562ca224fc2a9bbd3d9d587362c__section_a2b_33y_brb"/>

## Remarks

Auditing is the recording of details about many database events to the file container. Databases with auditing on can’t be started in read-only mode. If you require auditing for a larger set of auditing types than available in the SA\_ENABLE\_AUDITING\_TYPE system procedure, consider creating trace sessions instead.

For the AUDITING option to work, you must set the auditing option to ON, and use the SA\_ENABLE\_AUDITING\_TYPE system procedure to indicate the types of information to audit, including any combination of permission checks, connection attempts, DDL statements, public options, triggers. Auditing won’t take place if either of these conditions is true:

-   The AUDITING option is set to OFF
-   Auditing options have been disabled.

If you set the AUDITING option to ON, and don’t specify auditing options, all types of auditing information are recorded.



## Example

The following statement turns on auditing for the database.

```
SET OPTION PUBLIC.auditing = 'On';
```

**Related Information**  


[AUDITING Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/812cc49c6ce21014a5f195897313e166.html "Enables and disables auditing in the database.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[sa\_enable\_auditing\_type System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../060-system-procedures/sa-enable-auditing-type-system-procedure-for-data-lake-relational-engine-sap-hana-db-mana-7bde72c.md "Specifies which events to include in auditing.")

[Auditing Database Events](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_3_QRC/en-US/4c20fb59d0e848e09ffb191c9d2c0b16.html "Auditing tracks all of the activity performed on a data lake Relational Engine database.") :arrow_upper_right:

