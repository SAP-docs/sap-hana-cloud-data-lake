<!-- loio3be358cf6c5f1014b95e90fb59459beb -->

# SQLDA sqllen Field Values When Sending Data

The manner in which the length of the data being sent to the database is determined depends on the data type.



For non-long data types, the `sqllen` field of the `sqlvar` structure in the SQLDA represents the maximum size of the data buffer. For example, a column described as VARCHAR\(300\) will have a `sqllen` value of 300, representing the maximum length for that column. For blank-padded data types such as DT\_FIXCHAR, the `sqllen` field represents the maximum size of the data buffer. For fixed-size data types such as integers and DT\_TIMESTAMP\_ STRUCT, the `sqllen` field is ignored and the length need not be specified. For long data types, the `array_len` field specifies the maximum length of the data buffer. The `sqllen` field is never modified when you send or retrieve data.

Only the data types displayed in the table below are allowed. The DT\_DATE, DT\_TIME, and DT\_TIMESTAMP data types are treated the same as DT\_STRING when you send or retrieve information. The value is formatted as a character string in the current date format.


<table>
<tr>
<th valign="top">

Embedded SQL Data Type



</th>
<th valign="top">

Program Action to Set the Length



</th>
</tr>
<tr>
<td valign="top">

DT\_BIGINT



</td>
<td valign="top">

Fixed size. No action required.



</td>
</tr>
<tr>
<td valign="top">

DT\_BINARY\(n\)



</td>
<td valign="top">

Set the `len` field to the length in bytes of data in the `array` field of the BINARY structure. The maximum length is 32767.



</td>
</tr>
<tr>
<td valign="top">

DT\_BIT



</td>
<td valign="top">

Fixed size. No action required.



</td>
</tr>
<tr>
<td valign="top">

DT\_DATE



</td>
<td valign="top">

The length is determined by the terminating null character.



</td>
</tr>
<tr>
<td valign="top">

DT\_DOUBLE



</td>
<td valign="top">

Fixed size. No action required.



</td>
</tr>
<tr>
<td valign="top">

DT\_FIXCHAR\(n\)



</td>
<td valign="top">

The `sqllen` field determines the length in bytes of the `sqldata` area. The data must be blank-padded. The maximum length is 32767.



</td>
</tr>
<tr>
<td valign="top">

DT\_FLOAT



</td>
<td valign="top">

Fixed size. No action required.



</td>
</tr>
<tr>
<td valign="top">

DT\_INT



</td>
<td valign="top">

Fixed size. No action required.



</td>
</tr>
<tr>
<td valign="top">

DT\_LONGBINARY



</td>
<td valign="top">

The `sqllen` field is ignored. The `array_len` field specifies the maximum length of the `array` field. Set the `stored_len` field to the actual length in bytes of data in the `array` field. More than 32767 bytes can be sent.



</td>
</tr>
<tr>
<td valign="top">

DT\_LONGNVARCHAR



</td>
<td valign="top">

The `sqllen` field is ignored. The `array_len` field specifies the maximum length of the `array` field. Set the `stored_len` field to the actual length in bytes of data in the `array` field. More than 32767 bytes can be sent.



</td>
</tr>
<tr>
<td valign="top">

DT\_LONGVARCHAR



</td>
<td valign="top">

The `sqllen` field is ignored. The `array_len` field specifies the maximum length of the `array` field. Set the `stored_len` field to the actual length in bytes of data in the `array` field. More than 32767 bytes can be sent.



</td>
</tr>
<tr>
<td valign="top">

DT\_NFIXCHAR\(n\)



</td>
<td valign="top">

The `sqllen` field determines the length in bytes of the `sqldata` area. The data must be blank-padded. The maximum length is 32767.



</td>
</tr>
<tr>
<td valign="top">

DT\_NSTRING



</td>
<td valign="top">

The length is determined by the terminating null character.



</td>
</tr>
<tr>
<td valign="top">

DT\_NVARCHAR\(n\)



</td>
<td valign="top">

Set the `len` field to the length in bytes of data in the `array` field of the NVARCHAR structure.



</td>
</tr>
<tr>
<td valign="top">

DT\_SMALLINT



</td>
<td valign="top">

Fixed size. No action required.



</td>
</tr>
<tr>
<td valign="top">

DT\_STRING



</td>
<td valign="top">

The length is determined by the terminating null character.



</td>
</tr>
<tr>
<td valign="top">

DT\_TIME



</td>
<td valign="top">

The length is determined by the terminating null character.



</td>
</tr>
<tr>
<td valign="top">

DT\_TIMESTAMP



</td>
<td valign="top">

The length is determined by the terminating null character.



</td>
</tr>
<tr>
<td valign="top">

DT\_TIMESTAMP\_STRUCT



</td>
<td valign="top">

Fixed size. No action required.



</td>
</tr>
<tr>
<td valign="top">

DT\_UNSBIGINT



</td>
<td valign="top">

Fixed size. No action required.



</td>
</tr>
<tr>
<td valign="top">

DT\_UNSINT



</td>
<td valign="top">

Fixed size. No action required.



</td>
</tr>
<tr>
<td valign="top">

DT\_UNSSMALLINT



</td>
<td valign="top">

Fixed size. No action required.



</td>
</tr>
<tr>
<td valign="top">

DT\_VARCHAR\(n\)



</td>
<td valign="top">

Set the `len` field to the length in bytes of data in the `array` field of the VARCHAR structure. The maximum length is 32767.



</td>
</tr>
<tr>
<td valign="top">

DT\_VARIABLE



</td>
<td valign="top">

The length is determined by the terminating null character.



</td>
</tr>
</table>

