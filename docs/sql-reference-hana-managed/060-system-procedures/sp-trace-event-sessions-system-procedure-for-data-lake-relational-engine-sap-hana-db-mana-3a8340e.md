<!-- loio3a8340e1d6cd40ebbb3717c9530a2047 -->

# sp\_trace\_event\_sessions System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a list of the trace event sessions that are defined for the database.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user. It cannot be run using the REMOTE\_EXECUTE procedure.



```
sp_trace_event_sessions( [ <session_name> ] )
```



<a name="loio3a8340e1d6cd40ebbb3717c9530a2047__section_iyf_2l2_srb"/>

## Parameters

  *<session\_name\>* 
 :   Use this CHAR\(256\) parameter to specify the trace event session you want to get information about. If a session name is not specified, information is returned about all trace event sessions in the database.

 

<a name="loio3a8340e1d6cd40ebbb3717c9530a2047__section_ptt_2l2_srb"/>

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



<a name="loio3a8340e1d6cd40ebbb3717c9530a2047__section_wph_fl2_srb"/>

## Remarks

Start and stop trace event sessions manually by using the STATE clause of the ALTER TRACE EVENT SESSION statement.



## Privileges

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio3a8340e1d6cd40ebbb3717c9530a2047__section_i5x_fl2_srb"/>

## Side Effects

None



The following statement returns a list of trace event sessions for the current database:

```
SELECT * FROM dbo.sp_trace_event_sessions( );
```

**Related Information**  


[sp_trace_event_sessions System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/8179c9326ce210149a84c8b4621ed3d9.html "Returns a list of the trace event sessions that are defined for the database.") :arrow_upper_right:

