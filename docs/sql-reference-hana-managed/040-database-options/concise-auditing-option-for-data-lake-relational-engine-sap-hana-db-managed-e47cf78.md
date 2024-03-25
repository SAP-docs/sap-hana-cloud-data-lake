<!-- loioe47cf784a3274b41bbaaa416bcc07d97 -->

# CONCISE\_AUDITING Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls whether concise auditing or legacy auditing is used.



<a name="loioe47cf784a3274b41bbaaa416bcc07d97__section_bph_csj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user..
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioe47cf784a3274b41bbaaa416bcc07d97__section_ly5_lr5_zyb"/>

## Syntax

```
CONCISE_AUDITING  = ON|OFF;
```



<a name="loioe47cf784a3274b41bbaaa416bcc07d97__section_qhk_vv1_1zb"/>

## Allowed Values

ON, OFF



<a name="loioe47cf784a3274b41bbaaa416bcc07d97__section_t1h_fw1_1zb"/>

## Default

ON



<a name="loioe47cf784a3274b41bbaaa416bcc07d97__section_gpn_jw1_1zb"/>

## Privileges

Privilege Category: PUBLIC



### 


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


-   To set a database option temporarily, use the SET\_TEMPORARY\_OPTION procedure, which requires you be a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.

    -   See [SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md).





</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

-   Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



</dd>
</dl>



<a name="loioe47cf784a3274b41bbaaa416bcc07d97__section_jgv_mw1_1zb"/>

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



<a name="loioe47cf784a3274b41bbaaa416bcc07d97__section_vyf_pw1_1zb"/>

## Remarks

An instance restart is required if you change the option.

Concise auditing behavior was introduced in QRC 1/2024. Setting this option to OFF reverts to legacy auditing behavior, which is deprecated.

**Related Information**  


[Auditing Database Events](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_1_QRC/en-US/4c20fb59d0e848e09ffb191c9d2c0b16.html "Auditing tracks all of the activity performed on a data lake Relational Engine database.") :arrow_upper_right:

[CONCISE_AUDITING Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/742c50f6746f4fb488ed6498e203def4.html "Controls whether concise auditing or legacy auditing is used.") :arrow_upper_right:

