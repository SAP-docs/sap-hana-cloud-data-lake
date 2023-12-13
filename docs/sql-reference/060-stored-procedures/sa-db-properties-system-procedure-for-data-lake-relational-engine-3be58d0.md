<!-- loio3be58d086c5f1014925bf0cfadeb33ef -->

# sa\_db\_properties System Procedure for Data Lake Relational Engine

Reports database property information.



<a name="loio3be58d086c5f1014925bf0cfadeb33ef__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_db_properties(  );
```



## Parameters

None



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

The database ID number.

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

The database property number.

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

The database property name.

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

The database property description.

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

The database property value.

</td>
</tr>
</table>



## Remarks

If you specify a database ID, the sa\_db\_properties system procedure returns the database ID number and the PropNum, PropName, PropDescription, and Value for each available database property. Values are returned for all database properties and statistics related to databases. Valid properties with NULL values are also returned.

If *<dbidparm\>* is greater than zero, then database properties for the supplied database are returned. If *<dbidparm\>* is less than zero, then database properties for the current database are returned. If *<dbidparm\>* is not supplied or is NULL, then database properties for all databases running on the database server are returned.



## Privileges

Requires EXECUTE object-level privilege on the procedure.

To execute this procedure for other databases, also requires MONITOR system privilege.



## Side Effects

None



## Examples

This example uses the sa\_db\_properties system procedure to return a result set summarizing database properties for the database.

```
CALL sa_db_properties( );
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

PropDescription

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

2

</td>
<td valign="top">

BytesReceived

</td>
<td valign="top">

Bytes received by server

</td>
<td valign="top">

82369619

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

3

</td>
<td valign="top">

BytesReceivedUncomp

</td>
<td valign="top">

Bytes received after decompression

</td>
<td valign="top">

82369619

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

4

</td>
<td valign="top">

BytesSent

</td>
<td valign="top">

Bytes sent to client

</td>
<td valign="top">

182649602

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

5

</td>
<td valign="top">

BytesSentUncomp

</td>
<td valign="top">

Bytes sent before compression

</td>
<td valign="top">

182649602

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

10

</td>
<td valign="top">

CacheHits

</td>
<td valign="top">

Cache Hits

</td>
<td valign="top">

143588940

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

11

</td>
<td valign="top">

CacheReadIndInt

</td>
<td valign="top">

Cache index interior reads

</td>
<td valign="top">

5334621

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

12

</td>
<td valign="top">

CacheReadIndLeaf

</td>
<td valign="top">

Cache index leaf reads

</td>
<td valign="top">

31752948

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

16

</td>
<td valign="top">

CacheRead

</td>
<td valign="top">

Cache reads

</td>
<td valign="top">

143596017

</td>
</tr>
<tr>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
</tr>
</table>

