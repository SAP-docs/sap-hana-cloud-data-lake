<!-- loio3be575056c5f10148e5c8cb5b61644ff -->

# sa\_conn\_properties System Procedure for Data Lake Relational Engine

Reports connection property information.



<a name="loio3be575056c5f10148e5c8cb5b61644ff__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_conn_properties( [ <connidparm> ] );
```



## Parameters


<dl>
<dt><b>

*<connidparm\>* 

</b></dt>
<dd>

Use this optional INTEGER parameter to specify the connection ID number. The default is NULL.



</dd>
</dl>



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

Number

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Returns the connection ID \(a number\) for the current connection.

</td>
</tr>
<tr>
<td valign="top">

PropNum

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Returns the connection property number.

</td>
</tr>
<tr>
<td valign="top">

PropName

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

Returns the connection property name.

</td>
</tr>
<tr>
<td valign="top">

PropDescription

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

Returns the connection property description.

</td>
</tr>
<tr>
<td valign="top">

Value

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

Returns the connection property value.

</td>
</tr>
</table>



## Remarks

Returns the connection ID as Number, and the PropNum, PropName, PropDescription, and Value for each available connection property. Values are returned for all connection properties, database option settings related to connections, and statistics related to connections. Valid properties with NULL values are also returned.

If *<connidparm\>* is less than zero, then property values for the current connection are returned. If *<connidparm\>* is not supplied or is NULL, then property values are returned for all connections to the current database.



## Privileges

Require EXECUTE object-level privilege on the procedure.

To obtain a list of all connection IDs, you also need the MONITOR system privilege.



## Side Effects

None



## Examples

This example uses the sa\_conn\_properties system procedure to return a result set summarizing connection property information for all connections.

```
CALL sa_conn_properties( );
```


<table>
<tr>
<th valign="top">

Number

</th>
<th valign="top">

PropNum

</th>
<th valign="top">

PropName

</th>
<th valign="top">

...

</th>
</tr>
<tr>
<td valign="top">

79

</td>
<td valign="top">

37

</td>
<td valign="top">

ClientStmtCacheHits

</td>
<td valign="top">

...

</td>
</tr>
<tr>
<td valign="top">

79

</td>
<td valign="top">

38

</td>
<td valign="top">

ClientStmtCacheMisses

</td>
<td valign="top">

...

</td>
</tr>
<tr>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
</tr>
</table>

This example uses the sa\_conn\_properties system procedure to return a list of all connections, in decreasing order by CPU time\*:

```
SELECT Number AS connection_number,
    CONNECTION_PROPERTY ( 'Name', Number ) AS connection_name,
    CONNECTION_PROPERTY ( 'Userid', Number ) AS user_id,
  CAST ( Value AS NUMERIC ( 30, 2 ) ) AS approx_cpu_time
  FROM sa_conn_properties( )
  WHERE PropName = 'ApproximateCPUTime'
  ORDER BY approx_cpu_time DESC;
```

