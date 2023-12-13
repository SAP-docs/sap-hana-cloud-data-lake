<!-- loio0fe1a87371d7428b8eba1466ae8e4afa -->

# ALLOW\_OPTIONAL\_SEMICOLON\_IN\_TSQL Option

Controls the parsing of optional TSQL semicolons.



<a name="loio0fe1a87371d7428b8eba1466ae8e4afa__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio0fe1a87371d7428b8eba1466ae8e4afa__section_u1n_l5b_qkb"/>

## Syntax

```
ALLOW_OPTIONAL_SEMICOLON_IN_TSQL = { ON | OFF };
```



<a name="loio0fe1a87371d7428b8eba1466ae8e4afa__section_kyr_psr_zqb"/>

## Allowed Values

ON, OFF



<a name="loio0fe1a87371d7428b8eba1466ae8e4afa__section_lyr_psr_zqb"/>

## Default

ON



<a name="loio0fe1a87371d7428b8eba1466ae8e4afa__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio0fe1a87371d7428b8eba1466ae8e4afa__section_dqn_kmn_hrb"/>

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

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
</table>



<a name="loio0fe1a87371d7428b8eba1466ae8e4afa__section_myr_psr_zqb"/>

## Remarks

When enabled \(ON\), semicolons are allowed as optional statement delimiters in the TSQL dialect. Semicolons are not allowed as optional statement delimiters in TSQL and any procedure definitions affected by this change will be accepted by the parser.

This option can be set at the public scope only.

