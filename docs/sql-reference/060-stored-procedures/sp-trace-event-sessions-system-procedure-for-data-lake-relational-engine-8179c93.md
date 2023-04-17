<!-- loio8179c9326ce210149a84c8b4621ed3d9 -->

# sp\_trace\_event\_sessions System Procedure for Data Lake Relational Engine

Returns a list of the trace event sessions that are defined for the database.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_trace_event_sessions( [ <session_name> ] )
```



<a name="loio8179c9326ce210149a84c8b4621ed3d9__sp_trace_event_sessions_parm1"/>

## Parameters

  *<session\_name\>* 
 :   Use this CHAR\(256\) parameter to specify the trace event session you want to get information about. If a session name is not specified, information is returned about all trace event sessions in the database.

 

<a name="loio8179c9326ce210149a84c8b4621ed3d9__sp_trace_event_sessions_resultset1"/>

## Result Set


<table>
<tr>
<th valign="top">

Column name



</th>
<th valign="top">

Data type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

session\_name



</td>
<td valign="top">

CHAR\(256\)



</td>
<td valign="top">

Returns the name of the session.



</td>
</tr>
<tr>
<td valign="top">

description



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Returns a description of the session.



</td>
</tr>
<tr>
<td valign="top">

started



</td>
<td valign="top">

BIT



</td>
<td valign="top">

Returns 1 if the session has started and 0 otherwise.



</td>
</tr>
<tr>
<td valign="top">

is\_temporary



</td>
<td valign="top">

BIT



</td>
<td valign="top">

Returns 1 if the trace session is temporary and 0 otherwise.



</td>
</tr>
</table>



<a name="loio8179c9326ce210149a84c8b4621ed3d9__sp_trace_event_sessions_remarks1"/>

## Remarks

Start and stop trace event sessions manually by using the STATE clause of the ALTER TRACE EVENT SESSION statement.



## Privileges

You need to have the EXECUTE privilege on the system procedure, as well as the MANAGE ANY TRACE SESSION system privilege.



<a name="loio8179c9326ce210149a84c8b4621ed3d9__sp_trace_event_sessions_sideeffect1"/>

## Side Effects

None



The following statement returns a list of trace event sessions for the current database:

```
SELECT * FROM dbo.sp_trace_event_sessions( );
```

**Related Information**  


[sp_trace_event_sessions System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/3a8340e1d6cd40ebbb3717c9530a2047.html "Returns a list of the trace event sessions that are defined for the database.") :arrow_upper_right:

