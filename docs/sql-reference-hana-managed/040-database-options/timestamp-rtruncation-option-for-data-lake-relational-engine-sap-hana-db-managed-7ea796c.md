<!-- loio7ea796c77e5047c78acff41829be70aa -->

# TIMESTAMP\_RTRUNCATION Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls whether INSERT, UPDATE, or CAST operations on TIMESTAMP data type columns fails if loss of precision will result.



<a name="loio7ea796c77e5047c78acff41829be70aa__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio7ea796c77e5047c78acff41829be70aa__section_dgc_scr_f1c"/>

## Syntax

```
TIMESTAMP_RTRUNCATION = { ON | OFF };
```



<a name="loio7ea796c77e5047c78acff41829be70aa__section_m2p_tcr_f1c"/>

## Allowed Values

ON, OFF



<a name="loio7ea796c77e5047c78acff41829be70aa__section_gsh_5cr_f1c"/>

## Default

The default value of the TIMESTAMP\_RTRUNCATION database option depends on when your data lake Relational Engine instance was created.


<table>
<tr>
<th valign="top">

Default

</th>
<th valign="top">

Configuration

</th>
</tr>
<tr>
<td valign="top">

ON

</td>
<td valign="top">

-   The instance was created using version QRC 1/2024 or later.
-   A new relational container was created after a forced upgrade to version QRC 2/2023 or later.



</td>
</tr>
<tr>
<td valign="top">

OFF

</td>
<td valign="top">

-   The instance was created using a version prior to version QRC 1/2024.



</td>
</tr>
</table>



<a name="loio7ea796c77e5047c78acff41829be70aa__section_nkp_vcr_f1c"/>

## Privileges

Privilege Category: PUBLIC



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method and whether you are setting the option temporarily or permanently:


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



<a name="loio7ea796c77e5047c78acff41829be70aa__section_rly_wcr_f1c"/>

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



<a name="loio7ea796c77e5047c78acff41829be70aa__section_mql_ycr_f1c"/>

## Remarks

When enabled, any INSERT, UPDATE, or CAST operation on a timestamp data type column that will result in lost precision fails.

To determine the current value for the option, execute the following statement:

```
SELECT connection_property('Timestamp_rtruncation');
```

**Related Information**  


[Set a Database Option](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/0dcb8935b09946e99324f53dd0dc7346.html "You set options with the SET OPTION statement.") :arrow_upper_right:

[TIMESTAMP Data Type Precision in Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/520ce6c6c90f47769eb2f1ddafa8bf49.html "Precision conflicts between TIMESTAMP data types result in data loss.") :arrow_upper_right:

[Date and Time Data Types in Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a51e8fb484f210158a94c1c80914c51d.html "Use date and time data types for storing dates and times.") :arrow_upper_right:

[TIMESTAMP_RTRUNCATION Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/dbb08c71f0a34f93b2f28d765e123ed0.html "Controls whether INSERT, UPDATE, or CAST operations on TIMESTAMP data type columns fails if loss of precision will result.") :arrow_upper_right:

