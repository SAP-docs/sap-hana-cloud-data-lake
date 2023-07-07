<!-- loiob96926be0fc140889e7cefa3565b0f1f -->

# TEMP\_EXTRACT\_CONNECTION\_STRING Option \(Deprecated\) for Data Lake Relational Engine

Specifies the connection string of your Azure storage account.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loiob96926be0fc140889e7cefa3565b0f1f__temp_extract_connection_syntax1"/>

## Syntax

```
TEMP_EXTRACT_CONNECTION_STRING <string_expression>
```



<a name="loiob96926be0fc140889e7cefa3565b0f1f__temp_extract_connection_values1"/>

## Allowed Values

The Azure storage account connection string. Example connection string:

```
DefaultEndpointsProtocol=https;AccountName=example;AccountKey=example_key;EndpointSuffix=core.windows.net
```

> ### Tip:  
> You can find your connection string in Azure portal. From your storage account, navigate to *Settings* \> *Access Keys*. Locate the *Connection string* section and copy the connection string to the clipboard.



<a name="loiob96926be0fc140889e7cefa3565b0f1f__temp_extract_connection_default1"/>

## Default

Null



<a name="loiob96926be0fc140889e7cefa3565b0f1f__temp_extract_connection_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loiob96926be0fc140889e7cefa3565b0f1f__temp_extract_connection_scope1"/>

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



<a name="loiob96926be0fc140889e7cefa3565b0f1f__temp_extract_connection_remarks1"/>

## Remarks

Used when extracting data lake Relational Engine data to one or more block blobs in an Azure storage account container.

Doesn’t apply to Amazon S3 storage.

For example syntax, see *Extract Data Lake Relational Engine Table Data to Azure Blob Storage*.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/84a37a4b73ff4ba1ae53aad6b4c94803.html "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.") :arrow_upper_right:

[(Deprecated) Extract Table Data from Data Lake Relational Engine to Azure Blob Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_2_QRC/en-US/72f882141a704328a7ff18c7b0b1914e.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more block blobs in an Azure storage account container.") :arrow_upper_right:

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_2_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_CONNECTION_STRING Option (Deprecated) for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/102fce67fe5341fa983aca0a4e3143a7.html "Specifies the connection string of your Azure storage account.") :arrow_upper_right:

