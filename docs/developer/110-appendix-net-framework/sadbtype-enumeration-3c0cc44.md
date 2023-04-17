<!-- loio3c0cc4416c5f1014a69cec835e1ea570 -->

# SADbType Enumeration

Enumerates the database server .NET database data types.



Visual Basic
:   ```
Public Enum SADbType
```

C\#
:   ```
enum SADbType
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
</tr>
<tr>
<td valign="top">

BigInt



</td>
<td valign="top">

Signed 64-bit integer.



</td>
</tr>
<tr>
<td valign="top">

Binary



</td>
<td valign="top">

Binary data, with a specified maximum length.

The enumeration values Binary and VarBinary are aliases of each other.



</td>
</tr>
<tr>
<td valign="top">

Bit



</td>
<td valign="top">

1-bit flag.



</td>
</tr>
<tr>
<td valign="top">

Char



</td>
<td valign="top">

Character data, with a specified length.

This type always supports Unicode characters. The types Char and VarChar are fully compatible.



</td>
</tr>
<tr>
<td valign="top">

Date



</td>
<td valign="top">

Date information.



</td>
</tr>
<tr>
<td valign="top">

DateTime



</td>
<td valign="top">

Timestamp information \(date, time\).

The enumeration values DateTime and TimeStamp are aliases of each other.



</td>
</tr>
<tr>
<td valign="top">

DateTimeOffset



</td>
<td valign="top">

Timestamp information \(date, time\) offset.



</td>
</tr>
<tr>
<td valign="top">

Decimal



</td>
<td valign="top">

Exact numerical data, with a specified precision and scale.

The enumeration values Decimal and Numeric are aliases of each other.



</td>
</tr>
<tr>
<td valign="top">

Double



</td>
<td valign="top">

Double-precision floating-point number \(8 bytes\).



</td>
</tr>
<tr>
<td valign="top">

Float



</td>
<td valign="top">

Single-precision floating-point number \(4 bytes\).

The enumeration values Float and Real are aliases of each other.



</td>
</tr>
<tr>
<td valign="top">

Image



</td>
<td valign="top">

Stores binary data of arbitrary length.



</td>
</tr>
<tr>
<td valign="top">

Integer



</td>
<td valign="top">

Unsigned 32-bit integer.



</td>
</tr>
<tr>
<td valign="top">

LongBinary



</td>
<td valign="top">

Binary data, with variable length.



</td>
</tr>
<tr>
<td valign="top">

LongNVarchar



</td>
<td valign="top">

Character data in the NCHAR character set, with variable length.

This type always supports Unicode characters.



</td>
</tr>
<tr>
<td valign="top">

LongVarbit



</td>
<td valign="top">

Bit arrays, with variable length.



</td>
</tr>
<tr>
<td valign="top">

LongVarchar



</td>
<td valign="top">

Character data, with variable length.

This type always supports Unicode characters.



</td>
</tr>
<tr>
<td valign="top">

Money



</td>
<td valign="top">

Monetary data.



</td>
</tr>
<tr>
<td valign="top">

NChar



</td>
<td valign="top">

Stores Unicode character data, up to 32767 characters.



</td>
</tr>
<tr>
<td valign="top">

NText



</td>
<td valign="top">

Stores Unicode character data of arbitrary length.



</td>
</tr>
<tr>
<td valign="top">

Numeric



</td>
<td valign="top">

Exact numerical data, with a specified precision and scale.

The enumeration values Decimal and Numeric are aliases of each other.



</td>
</tr>
<tr>
<td valign="top">

NVarChar



</td>
<td valign="top">

Stores Unicode character data, up to 32767 characters.



</td>
</tr>
<tr>
<td valign="top">

Real



</td>
<td valign="top">

Single-precision floating-point number \(4 bytes\).

The enumeration values Float and Real are aliases of each other.



</td>
</tr>
<tr>
<td valign="top">

SmallDateTime



</td>
<td valign="top">

A domain, implemented as TIMESTAMP.



</td>
</tr>
<tr>
<td valign="top">

SmallInt



</td>
<td valign="top">

Signed 16-bit integer.



</td>
</tr>
<tr>
<td valign="top">

SmallMoney



</td>
<td valign="top">

Stores monetary data that is less than one million currency units.



</td>
</tr>
<tr>
<td valign="top">

SysName



</td>
<td valign="top">

Stores character data of arbitrary length.



</td>
</tr>
<tr>
<td valign="top">

Text



</td>
<td valign="top">

Stores character data of arbitrary length.



</td>
</tr>
<tr>
<td valign="top">

Time



</td>
<td valign="top">

Time information.



</td>
</tr>
<tr>
<td valign="top">

TimeStamp



</td>
<td valign="top">

Timestamp information \(date, time\).

The enumeration values DateTime and TimeStamp are aliases of each other.



</td>
</tr>
<tr>
<td valign="top">

TimeStampWithTimeZone



</td>
<td valign="top">

Timestamp information \(date, time, time zone\).

The enumeration values DateTime and TimeStamp are aliases of each other.



</td>
</tr>
<tr>
<td valign="top">

TinyInt



</td>
<td valign="top">

Unsigned 8-bit integer.



</td>
</tr>
<tr>
<td valign="top">

UniqueIdentifier



</td>
<td valign="top">

Universally Unique Identifier \(UUID/GUID\).



</td>
</tr>
<tr>
<td valign="top">

UniqueIdentifierStr



</td>
<td valign="top">

A domain, implemented as CHAR\( 36 \).

UniqueIdentifierStr is used for remote data access when mapping Microsoft SQL Server uniqueidentifier columns.



</td>
</tr>
<tr>
<td valign="top">

UnsignedBigInt



</td>
<td valign="top">

Unsigned 64-bit integer.



</td>
</tr>
<tr>
<td valign="top">

UnsignedInt



</td>
<td valign="top">

Unsigned 32-bit integer.



</td>
</tr>
<tr>
<td valign="top">

UnsignedSmallInt



</td>
<td valign="top">

Unsigned 16-bit integer.



</td>
</tr>
<tr>
<td valign="top">

VarBinary



</td>
<td valign="top">

Binary data, with a specified maximum length.

The enumeration values *Binary* and *VarBinary* are aliases of each other.



</td>
</tr>
<tr>
<td valign="top">

VarBit



</td>
<td valign="top">

Bit arrays that are from 1 to 32767 bits in length.



</td>
</tr>
<tr>
<td valign="top">

VarChar



</td>
<td valign="top">

Character data, with a specified maximum length.

This type always supports Unicode characters. The types Char and VarChar are fully compatible.



</td>
</tr>
<tr>
<td valign="top">

Xml



</td>
<td valign="top">

XML data.

This type stores character data of arbitrary length, and is used to store XML documents.



</td>
</tr>
</table>



## Remarks

The table below lists which .NET types are compatible with each SADbType. In the case of integral types, table columns can always be set using smaller integer types, but can also be set using larger types as long as the actual value is within the range of the type.


<table>
<tr>
<th valign="top">

SADbType



</th>
<th valign="top">

Compatible .NET type



</th>
<th valign="top">

C\# built-in type



</th>
<th valign="top">

Visual Basic built-in type



</th>
</tr>
<tr>
<td valign="top">

 *BigInt* 



</td>
<td valign="top">

System.Int64



</td>
<td valign="top">

long



</td>
<td valign="top">

Long



</td>
</tr>
<tr>
<td valign="top">

 *Binary*, *VarBinary* 



</td>
<td valign="top">

System.Byte\[\], or System.Guid if size is 16



</td>
<td valign="top">

byte\[\]



</td>
<td valign="top">

Byte\(\)



</td>
</tr>
<tr>
<td valign="top">

 *Bit* 



</td>
<td valign="top">

System.Boolean



</td>
<td valign="top">

bool



</td>
<td valign="top">

Boolean



</td>
</tr>
<tr>
<td valign="top">

 *Char*, *VarChar* 



</td>
<td valign="top">

System.String



</td>
<td valign="top">

String



</td>
<td valign="top">

String



</td>
</tr>
<tr>
<td valign="top">

 *Date* 



</td>
<td valign="top">

System.DateTime



</td>
<td valign="top">

DateTime \(no built-in type\)



</td>
<td valign="top">

Date



</td>
</tr>
<tr>
<td valign="top">

 *DateTime*, *TimeStamp* 



</td>
<td valign="top">

System.DateTime



</td>
<td valign="top">

DateTime \(no built-in type\)



</td>
<td valign="top">

DateTime



</td>
</tr>
<tr>
<td valign="top">

 *DateTimeOffset* 



</td>
<td valign="top">

System.DateTimeOffset



</td>
<td valign="top">

DateTimeOffset \(no built-in type\)



</td>
<td valign="top">

DateTimeOffset



</td>
</tr>
<tr>
<td valign="top">

 *Decimal*, *Numeric* 



</td>
<td valign="top">

System.String



</td>
<td valign="top">

decimal



</td>
<td valign="top">

Decimal



</td>
</tr>
<tr>
<td valign="top">

 *Double* 



</td>
<td valign="top">

System.Double



</td>
<td valign="top">

double



</td>
<td valign="top">

Double



</td>
</tr>
<tr>
<td valign="top">

 *Float*, *Real* 



</td>
<td valign="top">

System.Single



</td>
<td valign="top">

float



</td>
<td valign="top">

Single



</td>
</tr>
<tr>
<td valign="top">

 *Image* 



</td>
<td valign="top">

System.Byte\[\]



</td>
<td valign="top">

byte\[\]



</td>
<td valign="top">

Byte\(\)



</td>
</tr>
<tr>
<td valign="top">

 *Integer* 



</td>
<td valign="top">

System.Int32



</td>
<td valign="top">

int



</td>
<td valign="top">

Integer



</td>
</tr>
<tr>
<td valign="top">

 *LongBinary* 



</td>
<td valign="top">

System.Byte\[\]



</td>
<td valign="top">

byte\[\]



</td>
<td valign="top">

Byte\(\)



</td>
</tr>
<tr>
<td valign="top">

 *LongNVarChar* 



</td>
<td valign="top">

System.String



</td>
<td valign="top">

String



</td>
<td valign="top">

String



</td>
</tr>
<tr>
<td valign="top">

 *LongVarChar* 



</td>
<td valign="top">

System.String



</td>
<td valign="top">

String



</td>
<td valign="top">

String



</td>
</tr>
<tr>
<td valign="top">

 *Money* 



</td>
<td valign="top">

System.String



</td>
<td valign="top">

decimal



</td>
<td valign="top">

Decimal



</td>
</tr>
<tr>
<td valign="top">

 *NChar* 



</td>
<td valign="top">

System.String



</td>
<td valign="top">

String



</td>
<td valign="top">

String



</td>
</tr>
<tr>
<td valign="top">

 *NText* 



</td>
<td valign="top">

System.String



</td>
<td valign="top">

String



</td>
<td valign="top">

String



</td>
</tr>
<tr>
<td valign="top">

 *Numeric* 



</td>
<td valign="top">

System.String



</td>
<td valign="top">

decimal



</td>
<td valign="top">

Decimal



</td>
</tr>
<tr>
<td valign="top">

 *NVarChar* 



</td>
<td valign="top">

System.String



</td>
<td valign="top">

String



</td>
<td valign="top">

String



</td>
</tr>
<tr>
<td valign="top">

 *SmallDateTime* 



</td>
<td valign="top">

System.DateTime



</td>
<td valign="top">

DateTime \(no built-in type\)



</td>
<td valign="top">

Date



</td>
</tr>
<tr>
<td valign="top">

 *SmallInt* 



</td>
<td valign="top">

System.Int16



</td>
<td valign="top">

short



</td>
<td valign="top">

Short



</td>
</tr>
<tr>
<td valign="top">

 *SmallMoney* 



</td>
<td valign="top">

System.String



</td>
<td valign="top">

decimal



</td>
<td valign="top">

Decimal



</td>
</tr>
<tr>
<td valign="top">

 *SysName* 



</td>
<td valign="top">

System.String



</td>
<td valign="top">

String



</td>
<td valign="top">

String



</td>
</tr>
<tr>
<td valign="top">

 *Text* 



</td>
<td valign="top">

System.String



</td>
<td valign="top">

String



</td>
<td valign="top">

String



</td>
</tr>
<tr>
<td valign="top">

 *Time* 



</td>
<td valign="top">

System.TimeSpan



</td>
<td valign="top">

TimeSpan \(no built-in type\)



</td>
<td valign="top">

TimeSpan \(no built-in type\)



</td>
</tr>
<tr>
<td valign="top">

 *TimeStamp* 



</td>
<td valign="top">

System.DateTime



</td>
<td valign="top">

DateTime \(no built-in type\)



</td>
<td valign="top">

Date



</td>
</tr>
<tr>
<td valign="top">

 *TimeStampWithTimeZone* 



</td>
<td valign="top">

System.DateTimeOffset



</td>
<td valign="top">

DateTimeOffset \(no built-in type\)



</td>
<td valign="top">

DateTimeOffset



</td>
</tr>
<tr>
<td valign="top">

 *TinyInt* 



</td>
<td valign="top">

System.Byte



</td>
<td valign="top">

byte



</td>
<td valign="top">

Byte



</td>
</tr>
<tr>
<td valign="top">

 *UniqueIdentifier* 



</td>
<td valign="top">

System.Guid



</td>
<td valign="top">

Guid \(no built-in type\)



</td>
<td valign="top">

Guid \(no built-in type\)



</td>
</tr>
<tr>
<td valign="top">

 *UniqueIdentifierStr* 



</td>
<td valign="top">

System.String



</td>
<td valign="top">

String



</td>
<td valign="top">

String



</td>
</tr>
<tr>
<td valign="top">

 *UnsignedBigInt* 



</td>
<td valign="top">

System.UInt64



</td>
<td valign="top">

ulong



</td>
<td valign="top">

UInt64 \(no built-in type\)



</td>
</tr>
<tr>
<td valign="top">

 *UnsignedInt* 



</td>
<td valign="top">

System.UInt32



</td>
<td valign="top">

uint



</td>
<td valign="top">

UInt64 \(no built-in type\)



</td>
</tr>
<tr>
<td valign="top">

 *UnsignedSmallInt* 



</td>
<td valign="top">

System.UInt16



</td>
<td valign="top">

ushort



</td>
<td valign="top">

UInt64 \(no built-in type\)



</td>
</tr>
<tr>
<td valign="top">

 *Xml* 



</td>
<td valign="top">

System.Xml



</td>
<td valign="top">

String



</td>
<td valign="top">

String



</td>
</tr>
</table>

Binary columns of length 16 are fully compatible with the UniqueIdentifier type.

**Related Information**  


[GetFieldType\(int\) Method](getfieldtype-int-method-3c16794.md "Returns the Type that is the data type of the object.")

[GetDataTypeName\(int\) Method](getdatatypename-int-method-3c16492.md "Returns the name of the source data type.")

