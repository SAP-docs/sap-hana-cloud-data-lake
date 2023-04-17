<!-- loio9cf3679da7d31014836283f1d265d12e -->

# a\_sqlany\_native\_type Enumeration

An enumeration of the native types of values as described by the server.



```
enum a_sqlany_native_type
```



## Members


<table>
<tr>
<th valign="top">

Member name



</th>
<th valign="top">

Description



</th>
<th valign="top">

Value



</th>
</tr>
<tr>
<td valign="top">

DT\_BIGINT



</td>
<td valign="top">

64-bit signed integer.



</td>
<td valign="top">

608



</td>
</tr>
<tr>
<td valign="top">

DT\_BINARY



</td>
<td valign="top">

Varying length binary data with a two-byte length field. When sending data, you must set the length field. The maximum length is 32767 bytes when sending data. When fetching data, the database server sets the length field. The maximum length is 32765 bytes when fetching data.



</td>
<td valign="top">

524



</td>
</tr>
<tr>
<td valign="top">

DT\_BIT



</td>
<td valign="top">

8-bit signed integer.



</td>
<td valign="top">

624



</td>
</tr>
<tr>
<td valign="top">

DT\_DATE



</td>
<td valign="top">

Null-terminated character string that is a valid date.



</td>
<td valign="top">

384



</td>
</tr>
<tr>
<td valign="top">

DT\_DECIMAL



</td>
<td valign="top">

Packed decimal number \(proprietary format\).



</td>
<td valign="top">

484



</td>
</tr>
<tr>
<td valign="top">

DT\_DOUBLE



</td>
<td valign="top">

8-byte floating-point number.



</td>
<td valign="top">

480



</td>
</tr>
<tr>
<td valign="top">

DT\_FIXCHAR



</td>
<td valign="top">

Fixed-length blank-padded character string, in the CHAR character set. The maximum length, specified in bytes, is 32767. The data is not null-terminated.



</td>
<td valign="top">

452



</td>
</tr>
<tr>
<td valign="top">

DT\_FLOAT



</td>
<td valign="top">

4-byte floating-point number.



</td>
<td valign="top">

482



</td>
</tr>
<tr>
<td valign="top">

DT\_INT



</td>
<td valign="top">

32-bit signed integer.



</td>
<td valign="top">

496



</td>
</tr>
<tr>
<td valign="top">

DT\_LONGBINARY



</td>
<td valign="top">

Long binary data.



</td>
<td valign="top">

528



</td>
</tr>
<tr>
<td valign="top">

DT\_LONGNVARCHAR



</td>
<td valign="top">

Long varying length character string, in the NCHAR character set.



</td>
<td valign="top">

640



</td>
</tr>
<tr>
<td valign="top">

DT\_LONGVARCHAR



</td>
<td valign="top">

Long varying length character string, in the CHAR character set.



</td>
<td valign="top">

456



</td>
</tr>
<tr>
<td valign="top">

DT\_NFIXCHAR



</td>
<td valign="top">

Fixed-length blank-padded character string, in the NCHAR character set. The maximum length, specified in bytes, is 32767. The data is not null-terminated.



</td>
<td valign="top">

632



</td>
</tr>
<tr>
<td valign="top">

DT\_NOTYPE



</td>
<td valign="top">

No data type.



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

DT\_NSTRING



</td>
<td valign="top">

Null-terminated character string, in the NCHAR character set. The string is blank-padded if the database is initialized with blank-padded strings.



</td>
<td valign="top">

628



</td>
</tr>
<tr>
<td valign="top">

DT\_NVARCHAR



</td>
<td valign="top">

Varying length character string, in the NCHAR character set, with a two-byte length field. When sending data, you must set the length field. The maximum length is 32767 bytes when sending data. When fetching data, the database server sets the length field. The maximum length is 32765 bytes when fetching data. The data is not null-terminated or blank-padded.



</td>
<td valign="top">

636



</td>
</tr>
<tr>
<td valign="top">

DT\_SMALLINT



</td>
<td valign="top">

16-bit signed integer.



</td>
<td valign="top">

500



</td>
</tr>
<tr>
<td valign="top">

DT\_STRING



</td>
<td valign="top">

Null-terminated character string, in the CHAR character set. The string is blank-padded if the database is initialized with blank-padded strings.



</td>
<td valign="top">

460



</td>
</tr>
<tr>
<td valign="top">

DT\_TIME



</td>
<td valign="top">

Null-terminated character string that is a valid time.



</td>
<td valign="top">

388



</td>
</tr>
<tr>
<td valign="top">

DT\_TIMESTAMP



</td>
<td valign="top">

Null-terminated character string that is a valid timestamp.



</td>
<td valign="top">

392



</td>
</tr>
<tr>
<td valign="top">

DT\_TINYINT



</td>
<td valign="top">

8-bit signed integer.



</td>
<td valign="top">

604



</td>
</tr>
<tr>
<td valign="top">

DT\_UNSBIGINT



</td>
<td valign="top">

64-bit unsigned integer.



</td>
<td valign="top">

620



</td>
</tr>
<tr>
<td valign="top">

DT\_UNSINT



</td>
<td valign="top">

32-bit unsigned integer.



</td>
<td valign="top">

612



</td>
</tr>
<tr>
<td valign="top">

DT\_UNSSMALLINT



</td>
<td valign="top">

16-bit unsigned integer.



</td>
<td valign="top">

616



</td>
</tr>
<tr>
<td valign="top">

DT\_VARCHAR



</td>
<td valign="top">

Varying length character string, in the CHAR character set, with a two-byte length field. When sending data, you must set the length field. The maximum length is 32767 bytes when sending data. When fetching data, the database server sets the length field. The maximum length is 32765 bytes when fetching data. The data is not null-terminated or blank-padded.



</td>
<td valign="top">

448



</td>
</tr>
</table>



## Remarks

The value types correspond to the embedded SQL data types.

**Related Information**  


[sqlany\_get\_column\_info\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_column\_info \*\) Method](sqlany-get-column-info-a-sqlany-stmt-sacapi-u32-a-sqlany-column-info-method-3bf6131.md "Retrieves column metadata information and fills the a_sqlany_column_info structure with information about the column.")

[a\_sqlany\_column\_info Structure](a-sqlany-column-info-structure-3bf4465.md "Returns column metadata information.")

