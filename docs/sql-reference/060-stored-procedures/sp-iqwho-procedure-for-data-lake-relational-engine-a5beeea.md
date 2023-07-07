<!-- loioa5beeead84f210158043f99faa62fce2 -->

# sp\_iqwho Procedure for Data Lake Relational Engine

Displays information about all current users and connections, or about a particular user or connection.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqwho [ { <connhandle> | <user-name> } [, <arg-type> ] ]
```



## Parameters


<dl>
<dt><b>

*<connhandle\>*

</b></dt>
<dd>

An integer representing the connection ID. If this parameter is specified, sp\_iqwho returns information only about the specified connection. If the specified connection is not open, no rows are displayed in the output.



</dd><dt><b>

*<user-name\>*

</b></dt>
<dd>

A char\(255\) parameter representing a user login name. If this parameter is specified, sp\_iqwho returns information only about the specified user. If the specified user has not opened any connections, no rows are displayed in the output. If the specified user name does not exist in the database, sp\_iqwho returns the error message "***User *<user-name\>* does not exist.***"



</dd><dt><b>

*<arg-type\>*

</b></dt>
<dd>

\(Optional\) Can be specified only when the first parameter has been specified. The only value for *<arg-type\>* is "user". If the *<arg-type\>* value is specified as "user", sp\_iqwho interprets the first parameter as a user name, even if the first parameter is numeric. If any value other than "user" is specified for *<arg-type\>*, sp\_iqwho returns the error "***Invalid parameter.***"

Enclose the *<arg-type\>* value in double quotes.



</dd>
</dl>



<a name="loioa5beeead84f210158043f99faa62fce2__section_cmh_kgg_nbb"/>

## Returns


<table>
<tr>
<th valign="top">

Column Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

ConnHandle



</td>
<td valign="top">

The SAP SQL Anywhere connection handle



</td>
</tr>
<tr>
<td valign="top">

IQConnID



</td>
<td valign="top">

The data lake Relational Engine specific connection ID.



</td>
</tr>
<tr>
<td valign="top">

Userid



</td>
<td valign="top">

The name of the user that opened the connection "ConnHandle".



</td>
</tr>
<tr>
<td valign="top">

BlockedOn



</td>
<td valign="top">

The connection on which a particular connection is blocked; 0 if not blocked on any connection.



</td>
</tr>
<tr>
<td valign="top">

BlockUserid



</td>
<td valign="top">

The owner of the blocking connection; NULL if there is no blocking connection.



</td>
</tr>
<tr>
<td valign="top">

ReqType



</td>
<td valign="top">

The type of the request made through the connection; DO\_NOTHING if no command is issued.



</td>
</tr>
<tr>
<td valign="top">

IQCmdType



</td>
<td valign="top">

The type of data lake Relational Engine command issued from the connection; NONE if no command is issued.



</td>
</tr>
<tr>
<td valign="top">

IQIdle



</td>
<td valign="top">

The time in seconds since the last data lake Relational Engine command was issued through the connection; in case of no last data lake Relational Engine command, the time since '01-01-2000' is displayed.



</td>
</tr>
<tr>
<td valign="top">

SAIdle



</td>
<td valign="top">

The time in seconds since the last SA request was issued through the connection; in case of no last SA command, the time since '01-01-2000' is displayed.



</td>
</tr>
<tr>
<td valign="top">

IQCursors



</td>
<td valign="top">

The number of active cursors in the connection; 0 if no cursors.



</td>
</tr>
<tr>
<td valign="top">

IQThreads



</td>
<td valign="top">

The number of threads with the connection. At least one thread is started as soon as the connection is opened, so the minimum value for IQThreads is 1.



</td>
</tr>
<tr>
<td valign="top">

TempTableSpaceKB



</td>
<td valign="top">

The size of temporary table space in kilobytes; 0 if no temporary table space is used



</td>
</tr>
<tr>
<td valign="top">

TempWorkSpaceKB



</td>
<td valign="top">

The size of temporary workspace in kilobytes; 0 if no temporary workspace is used



</td>
</tr>
</table>



<a name="loioa5beeead84f210158043f99faa62fce2__iq_refbb_1851"/>

## Remarks

The sp\_iqwho stored procedure displays information about all current users and connections, or about a particular user or connection.

The following lists a mapping of sp\_who and sp\_iqwho columns:


<table>
<tr>
<th valign="top">

sp\_who Column



</th>
<th valign="top">

sp\_iqwho Column



</th>
</tr>
<tr>
<td valign="top">

fid



</td>
<td valign="top">

Family to which a lock belongs; omitted, as not applicable to data lake Relational Engine



</td>
</tr>
<tr>
<td valign="top">

spid



</td>
<td valign="top">

ConnHandle, IQConnID



</td>
</tr>
<tr>
<td valign="top">

status



</td>
<td valign="top">

IQIdle, SAIdle



</td>
</tr>
<tr>
<td valign="top">

loginame



</td>
<td valign="top">

Userid



</td>
</tr>
<tr>
<td valign="top">

origname



</td>
<td valign="top">

User alias; omitted, as not applicable to data lake Relational Engine



</td>
</tr>
<tr>
<td valign="top">

hostname



</td>
<td valign="top">

Name of the host on which the server is running; currently not supported



</td>
</tr>
<tr>
<td valign="top">

blk\_spid



</td>
<td valign="top">

BlockedOn



</td>
</tr>
<tr>
<td valign="top">

dbname



</td>
<td valign="top">

Omitted, as there is one server and one database for data lake Relational Engine and they are the same for every connection



</td>
</tr>
<tr>
<td valign="top">

cmd



</td>
<td valign="top">

ReqType, IQCmdType



</td>
</tr>
<tr>
<td valign="top">

block\_xloid



</td>
<td valign="top">

BlockUserid



</td>
</tr>
</table>

If no parameters are specified, sp\_iqwho displays information about all currently active connections and users.

Either a connection handle or a user name can be specified as the first sp\_iqwho parameter. The parameters *<connhandle\>* and *<user-name\>* are exclusive and optional. Only one of these parameters can be specified at a time. By default, if the first parameter is numeric, the parameter is assumed to be a connection handle. If the first parameter is not numeric, it is assumed to be a user name.

Data lake Relational Engine allows numeric user names. The *<arg-type\>* parameter directs sp\_iqwho to interpret a numeric value in the first parameter as a user name. For example:

```
sp_iqwho 1, "user"
```

When the *<arg-type\>* "user" is specified, sp\_iqwho interprets the first parameter 1as a user name, not as a connection ID. If a user named 1 exists in the database, sp\_iqwho displays information about connections opened by user 1.


<table>
<tr>
<th valign="top">

Syntax



</th>
<th valign="top">

Output



</th>
</tr>
<tr>
<td valign="top">

sp\_iqwho



</td>
<td valign="top">

Displays all active connections



</td>
</tr>
<tr>
<td valign="top">

sp\_iqwho 3



</td>
<td valign="top">

Displays information about connection 3



</td>
</tr>
<tr>
<td valign="top">

sp\_iqwho "HDLADMIN"



</td>
<td valign="top">

Displays connections opened by user HDLADMIN



</td>
</tr>
<tr>
<td valign="top">

sp\_iqwho 3, "user"



</td>
<td valign="top">

Interprets 3 as a user name and displays connections opened by user 3. If user 3 does not exist, returns the error "***User 3 does not exist.***"



</td>
</tr>
<tr>
<td valign="top">

sp\_iqwho non-existing-user



</td>
<td valign="top">

Returns error "***User non-existing-user does not exist."***



</td>
</tr>
<tr>
<td valign="top">

sp\_iqwho 3, "xyz"



</td>
<td valign="top">

Returns the error "***Invalid parameter: xyz.***"



</td>
</tr>
</table>



<a name="loioa5beeead84f210158043f99faa62fce2__iq_refbb_1850"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with the MONITOR system privilege.



## Side Effects

None



## Standards

The data lake Relational Engine sp\_iqwho stored procedure incorporates the data lake Relational Engine equivalents of columns displayed by the SAP Adaptive Server Enterprise sp\_who procedure.

Some SAP ASE columns are omitted, as they are not applicable to data lake Relational Engine.



## Example

The following example displays all active connections:

```
ConnHandle IQConnID Userid      ReqType      IQCmdType            BlockedOn BlockUserid IQCursors
12         118      HDLADMIN    CURSOR_OPEN  IQUTILITYOPENCURSOR  0         (NULL)      0  
13         119      shweta      DO_NOTHING   NONE                 0         (NULL)      0


IQThreads IQIdle   SAIdle TempTableSpaceKB TempWorkSpaceKB
1         1          0       0             0
1         16238757   470     0             0
```

