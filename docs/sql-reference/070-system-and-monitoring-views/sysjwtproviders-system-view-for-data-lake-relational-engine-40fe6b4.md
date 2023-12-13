<!-- loio40fe6b4c8fe54af39a008dcc5fd5cd2b -->

# SYSJWTPROVIDERS System View for Data Lake Relational Engine

Lists JWT providers configured in the data lake Relational Engine database. The underlying system table for this view is ISYSJWTPROVIDERS.



<a name="loio40fe6b4c8fe54af39a008dcc5fd5cd2b__section_i2m_qpq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The ID of the JWT provider.

</td>
</tr>
<tr>
<td valign="top">

jwt\_provider\_name

</td>
<td valign="top">

VARCHAR\(256\)

</td>
<td valign="top">

The name of the JWT provider.

</td>
</tr>
<tr>
<td valign="top">

issuer\_name

</td>
<td valign="top">

VARCHAR\(512\)

</td>
<td valign="top">

The issuer name of the JWT provider.

</td>
</tr>
<tr>
<td valign="top">

external\_identity\_claim

</td>
<td valign="top">

VARCHAR\(256\)

</td>
<td valign="top">

The claim provided in the JWT tokens to use for mapping the JWT user name to the data lake Relational Engine database user.

</td>
</tr>
<tr>
<td valign="top">

priority

</td>
<td valign="top">

UNSIGNED SMALLINT

</td>
<td valign="top">

The priority of the JWT provider.

</td>
</tr>
</table>

**Related Information**  


[SYSJWTLOGINMAP System View for Data Lake Relational Engine](sysjwtloginmap-system-view-for-data-lake-relational-engine-d5978ec.md "Lists the JWT-user mappings configured in the data lake Relational Engine database. The underlying system table for this view is ISYSJWTLOGINMAP.")

[CREATE JWT PROVIDER Statement for Data Lake Relational Engine](../080-sql-statements/create-jwt-provider-statement-for-data-lake-relational-engine-49b7ee1.md "Defines a JWT provider in the data lake Relational Engine database.")

[ALTER JWT PROVIDER Statement for Data Lake Relational Engine](../080-sql-statements/alter-jwt-provider-statement-for-data-lake-relational-engine-f6b0a31.md "Alters a JWT provider in the data lake Relational Engine database.")

