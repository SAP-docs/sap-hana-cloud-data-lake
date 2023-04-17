<!-- loio8174a4ee6ce2101494b4d7376051cefd -->

# sa\_db\_option System Procedure for Data Lake Relational Engine

Overrides a database option while the database is running.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_db_option( 
<opt> 
, <val> 
)
```



## Parameters

  *<opt\>* 
 :   Use this CHAR\(128\) parameter to specify a database option name.

   *<val\>* 
 :   Use this LONG VARCHAR parameter to specify the new value for the database option.

 

## Remarks

Database administrators can use this procedure to override some database options temporarily, without restarting the database.

The option values that are changed using this procedure are reset to their default values when the database shuts down. To change an option value every time the database is started, specify the corresponding database option when the database is started \(if one exists\).

The following option settings can be changed:


<table>
<tr>
<th valign="top">

Option name



</th>
<th valign="top">

Values



</th>
<th valign="top">

System privilege



</th>
<th valign="top">

Additional information



</th>
</tr>
<tr>
<td valign="top">

DiskSandbox



</td>
<td valign="top">

ON, OFF



</td>
<td valign="top">

SERVER OPERATOR



</td>
<td valign="top">

When DiskSandbox is set to ON, it restricts read-write file operations on the database to the directory where the main database file is located and any subdirectories of this directory. To use the sa\_db\_option system procedure to change disk sandbox settings, you must provide the secured feature key for the manage\_disk\_sandbox feature.



</td>
</tr>
<tr>
<td valign="top">

PropertyHistoryList



</td>
<td valign="top">

comma-delimited list of database server properties



</td>
<td valign="top">

MANAGE PROPERTY HISTORY



</td>
<td valign="top">

When PropertyHistoryList is turned on, a default list of properties is selected. You can specify a comma-delimited list of database server properties to track. The default is an empty list.

If this option is not set then only properties tracked by the database server or by other databases on the same database server can be queried.

If the memory required to track all specified properties is greater than the limit set by the PropertyHistorySize database server option or by the available memory, then an error is raised and the property list is not modified for the database.



</td>
</tr>
<tr>
<td valign="top">

CollectStmtPerfStats



</td>
<td valign="top">

ON, OFF



</td>
<td valign="top">

MONITOR



</td>
<td valign="top">

When CollectStmtPerfStats is set to ON, it collects statement performance summary information. When it is set to OFF, it stops data collection and discards data that has been collected.



</td>
</tr>
</table>



## Privileges

You need to have the EXECUTE privilege on the system procedure, as well as the SERVER OPERATOR system privilege.



## Side Effects

None.



For the following example to work, the database server must be started with the option -sk securefkey.

This example enables the SYSTEM secured feature key that includes MANAGE\_KEYS, creates a new secured feature key called SECURITY with case-sensitive authorization code NewSecurityCode, and then uses the new secured feature key to enable the DiskSandbox option.

```
CALL sp_use_secure_feature_key( 'system', 'securefkey' );
CALL sp_create_secure_feature_key( 'security', 'NewSecurityCode', 'manage_security' );
CALL sp_use_secure_feature_key( 'security', 'NewSecurityCode' );
CALL sa_db_option( 'DiskSandbox', 'on' );
```

