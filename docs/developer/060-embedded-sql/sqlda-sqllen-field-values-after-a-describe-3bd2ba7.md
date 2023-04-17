<!-- loio3bd2ba776c5f1014897e87e16737fc4b -->

# SQLDA sqllen Field Values After a DESCRIBE

The DESCRIBE statement gets information about the host variables required to store data retrieved from the database, or host variables required to pass data to the database.



The following table indicates the values of the sqllen and sqltype structure members returned by the DESCRIBE statement for the various database types \(both SELECT LIST and BIND VARIABLE DESCRIBE statements\). For a user-defined database data type, the base type is described.

Your program can use the types and lengths returned from a DESCRIBE, or you may use another type. The database server performs type conversions between any two types. The memory pointed to by the sqldata field must correspond to the sqltype and sqllen fields. The Embedded SQL type is obtained by a bitwise AND of sqltype with DT\_TYPES \(sqltype & DT\_TYPES\).


<table>
<tr>
<th valign="top">

Database Field Type



</th>
<th valign="top">

Embedded SQL Type Returned



</th>
<th valign="top">

Length \(in Bytes\) Returned on Describe



</th>
</tr>
<tr>
<td valign="top">

BIGINT



</td>
<td valign="top">

DT\_BIGINT



</td>
<td valign="top">

8



</td>
</tr>
<tr>
<td valign="top">

BINARY\(n\)



</td>
<td valign="top">

DT\_BINARY



</td>
<td valign="top">

n



</td>
</tr>
<tr>
<td valign="top">

BIT



</td>
<td valign="top">

DT\_BIT



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

CHAR\(n\)



</td>
<td valign="top">

DT\_FIXCHAR<sup>1</sup> 



</td>
<td valign="top">

n times maximum data expansion when converting from database character set to the client's CHAR character set. If this length would be more than 32767 bytes, then the Embedded SQL type returned is DT\_LONGVARCHAR with a length of 32767 bytes.



</td>
</tr>
<tr>
<td valign="top">

CHAR\(n CHAR\)



</td>
<td valign="top">

DT\_FIXCHAR<sup>1</sup> 



</td>
<td valign="top">

n times maximum character length in the client's CHAR character set. If this length would be more than 32767 bytes, then the Embedded SQL type returned is DT\_LONGVARCHAR with a length of 32767 bytes.



</td>
</tr>
<tr>
<td valign="top">

DATE



</td>
<td valign="top">

DT\_DATE



</td>
<td valign="top">

length of longest formatted string



</td>
</tr>
<tr>
<td valign="top">

DECIMAL\(p,s\)



</td>
<td valign="top">

DT\_DECIMAL



</td>
<td valign="top">

low byte of length field in SQLDA set to p, and high byte set to s. See PRECISION and SCALE macros in sqlda.h.



</td>
</tr>
<tr>
<td valign="top">

DOUBLE



</td>
<td valign="top">

DT\_DOUBLE



</td>
<td valign="top">

8



</td>
</tr>
<tr>
<td valign="top">

FLOAT



</td>
<td valign="top">

DT\_FLOAT



</td>
<td valign="top">

4



</td>
</tr>
<tr>
<td valign="top">

INT



</td>
<td valign="top">

DT\_INT



</td>
<td valign="top">

4



</td>
</tr>
<tr>
<td valign="top">

LONG BINARY



</td>
<td valign="top">

DT\_LONGBINARY



</td>
<td valign="top">

32767



</td>
</tr>
<tr>
<td valign="top">

LONG NVARCHAR



</td>
<td valign="top">

DT\_LONGVARCHAR / DT\_LONGNVARCHAR<sup>2</sup> 



</td>
<td valign="top">

32767



</td>
</tr>
<tr>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

DT\_LONGVARCHAR



</td>
<td valign="top">

32767



</td>
</tr>
<tr>
<td valign="top">

NCHAR\(n\)



</td>
<td valign="top">

DT\_FIXCHAR / DT\_NFIXCHAR<sup>2</sup> 



</td>
<td valign="top">

n times maximum character length in the client's NCHAR character set. If this length would be more than 32767 bytes, then the Embedded SQL type returned is DT\_LONGNVARCHAR with a length of 32767 bytes.



</td>
</tr>
<tr>
<td valign="top">

NVARCHAR\(n\)



</td>
<td valign="top">

DT\_VARCHAR / DT\_NVARCHAR<sup>2</sup> 



</td>
<td valign="top">

n times maximum character length in the client's NCHAR character set. If this length would be more than 32767 bytes, then the Embedded SQL type returned is DT\_LONGNVARCHAR with a length of 32767 bytes.



</td>
</tr>
<tr>
<td valign="top">

REAL



</td>
<td valign="top">

DT\_FLOAT



</td>
<td valign="top">

4



</td>
</tr>
<tr>
<td valign="top">

SMALLINT



</td>
<td valign="top">

DT\_SMALLINT



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

TIME



</td>
<td valign="top">

DT\_TIME



</td>
<td valign="top">

length of longest formatted string



</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

DT\_TIMESTAMP



</td>
<td valign="top">

length of longest formatted string



</td>
</tr>
<tr>
<td valign="top">

TINYINT



</td>
<td valign="top">

DT\_TINYINT



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

DT\_UNSBIGINT



</td>
<td valign="top">

8



</td>
</tr>
<tr>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

DT\_UNSINT



</td>
<td valign="top">

4



</td>
</tr>
<tr>
<td valign="top">

UNSIGNED SMALLINT



</td>
<td valign="top">

DT\_UNSSMALLINT



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

VARCHAR\(n\)



</td>
<td valign="top">

DT\_VARCHAR<sup>1</sup> 



</td>
<td valign="top">

n times maximum data expansion when converting from database character set to the client's CHAR character set. If this length would be more than 32767 bytes, then the Embedded SQL type returned is DT\_LONGVARCHAR with a length of 32767 bytes.



</td>
</tr>
<tr>
<td valign="top">

VARCHAR\(n CHAR\)



</td>
<td valign="top">

DT\_VARCHAR<sup>1</sup> 



</td>
<td valign="top">

n times maximum character length in the client's CHAR character set. If this length would be more than 32767, then the Embedded SQL type returned is DT\_LONGVARCHAR with length 32767.



</td>
</tr>
</table>

 <sup>1</sup> The type returned for CHAR and VARCHAR may be DT\_LONGVARCHAR if the maximum byte length in the client's CHAR character set is greater than 32767 bytes.

 <sup>2</sup> The type returned for NCHAR and NVARCHAR may be DT\_LONGNVARCHAR if the maximum byte length in the client's NCHAR character set is greater than 32767 bytes. NCHAR, NVARCHAR, and LONG NVARCHAR are described by default as either DT\_FIXCHAR, DT\_VARCHAR, or DT\_LONGVARCHAR, respectively. If the db\_change\_nchar\_charset function has been called, the types are described as DT\_NFIXCHAR, DT\_NVARCHAR, and DT\_LONGNVARCHAR, respectively.

