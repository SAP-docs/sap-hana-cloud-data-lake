<!-- loio765761f7c3034452952eff4936be94a3 -->

# SYSJWTPROVIDERCMPCLAIMS System View for Data Lake Relational Engine

Lists claims set in JWT providers. The underlying system table for this view is ISYSJWTPROVIDERCMPCLAIMS.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




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

claim



</td>
<td valign="top">

VARCHAR\(256\)



</td>
<td valign="top">

The name of the claim.



</td>
</tr>
<tr>
<td valign="top">

operation



</td>
<td valign="top">

VARCHAR\(64\)



</td>
<td valign="top">

The operation used to compare the claim and value: EQUALS or HAS MEMBER.



</td>
</tr>
<tr>
<td valign="top">

value



</td>
<td valign="top">

VARCHAR\(512\)



</td>
<td valign="top">

The value of the claim.



</td>
</tr>
</table>

**Related Information**  


[SYSJWTLOGINMAP System View for Data Lake Relational Engine](sysjwtloginmap-system-view-for-data-lake-relational-engine-d5978ec.md "Lists the JWT-user mappings configured in the data lake Relational Engine database. The underlying system table for this view is ISYSJWTLOGINMAP.")

[SYSJWTPROVIDERS System View for Data Lake Relational Engine](sysjwtproviders-system-view-for-data-lake-relational-engine-40fe6b4.md "Lists JWT providers configured in the data lake Relational Engine database. The underlying system table for this view is ISYSJWTPROVIDERS.")

[CREATE JWT PROVIDER Statement for Data Lake Relational Engine](../080-sql-statements/create-jwt-provider-statement-for-data-lake-relational-engine-49b7ee1.md "Defines a JWT provider in the data lake Relational Engine database.")

[ALTER JWT PROVIDER Statement for Data Lake Relational Engine](../080-sql-statements/alter-jwt-provider-statement-for-data-lake-relational-engine-f6b0a31.md "Alters a JWT provider in the data lake Relational Engine database.")

