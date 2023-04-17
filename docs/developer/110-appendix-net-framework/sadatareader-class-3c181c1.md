<!-- loio3c181c1e6c5f1014b00493552557195c -->

# SADataReader Class

A read-only, forward-only result set from a query or stored procedure.



Visual Basic
:   ```
Public NotInheritable Class SADataReader Inherits System.Data.Common.DbDataReader Implements System.ComponentModel.IListSource
```

C\#
:   ```
public sealed class SADataReader : System.Data.Common.DbDataReader, System.ComponentModel.IListSource
```



## Members

All members of SADataReader, including inherited members.

 **Methods** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Method



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

public override void



</td>
<td valign="top">

 [Close\(\)](close-method-3c1600c.md) 



</td>
<td valign="top">

Closes the SADataReader.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [GetBoolean\(int\)](getboolean-int-method-3c16189.md) 



</td>
<td valign="top">

Returns the value of the specified column as a Boolean.



</td>
</tr>
<tr>
<td valign="top">

public override byte



</td>
<td valign="top">

 [GetByte\(int\)](getbyte-int-method-3c16205.md) 



</td>
<td valign="top">

Returns the value of the specified column as a Byte.



</td>
</tr>
<tr>
<td valign="top">

public override unsafe long



</td>
<td valign="top">

 [GetBytes\(int, long, byte\[\], int, int\)](getbytes-int-long-byte-int-int-method-3c16280.md) 



</td>
<td valign="top">

Reads a stream of bytes from the specified column offset into the buffer as an array, starting at the given buffer offset.



</td>
</tr>
<tr>
<td valign="top">

public override char



</td>
<td valign="top">

 [GetChar\(int\)](getchar-int-method-3c1630c.md) 



</td>
<td valign="top">

Returns the value of the specified column as a character.



</td>
</tr>
<tr>
<td valign="top">

public override unsafe long



</td>
<td valign="top">

 [GetChars\(int, long, char\[\], int, int\)](getchars-int-long-char-int-int-method-3c16388.md) 



</td>
<td valign="top">

Reads a stream of characters from the specified column offset into the buffer as an array starting at the given buffer offset.



</td>
</tr>
<tr>
<td valign="top">

public new IDataReader



</td>
<td valign="top">

 [GetData\(int\)](getdata-int-method-3c16416.md) 



</td>
<td valign="top">

This method is not supported.



</td>
</tr>
<tr>
<td valign="top">

public override string



</td>
<td valign="top">

 [GetDataTypeName\(int\)](getdatatypename-int-method-3c16492.md) 



</td>
<td valign="top">

Returns the name of the source data type.



</td>
</tr>
<tr>
<td valign="top">

public override DateTime



</td>
<td valign="top">

 [GetDateTime\(int\)](getdatetime-int-method-3c1651f.md) 



</td>
<td valign="top">

Returns the value of the specified column as a DateTime object.



</td>
</tr>
<tr>
<td valign="top">

public DateTimeOffset



</td>
<td valign="top">

 [GetDateTimeOffset\(int\)](getdatetimeoffset-int-method-3c1659e.md) 



</td>
<td valign="top">

Returns the value of the specified column as a DateTimeOffset object.



</td>
</tr>
<tr>
<td valign="top">

public override decimal



</td>
<td valign="top">

 [GetDecimal\(int\)](getdecimal-int-method-3c16617.md) 



</td>
<td valign="top">

Returns the value of the specified column as a Decimal object.



</td>
</tr>
<tr>
<td valign="top">

public override double



</td>
<td valign="top">

 [GetDouble\(int\)](getdouble-int-method-3c16698.md) 



</td>
<td valign="top">

Returns the value of the specified column as a double-precision floating-point number.



</td>
</tr>
<tr>
<td valign="top">

public override IEnumerator



</td>
<td valign="top">

 [GetEnumerator\(\)](getenumerator-method-3c16716.md) 



</td>
<td valign="top">

Returns a System.Collections.IEnumerator that iterates through the SADataReader object.



</td>
</tr>
<tr>
<td valign="top">

public override Type



</td>
<td valign="top">

 [GetFieldType\(int\)](getfieldtype-int-method-3c16794.md) 



</td>
<td valign="top">

Returns the Type that is the data type of the object.



</td>
</tr>
<tr>
<td valign="top">

public override float



</td>
<td valign="top">

 [GetFloat\(int\)](getfloat-int-method-3c1680d.md) 



</td>
<td valign="top">

Returns the value of the specified column as a single-precision floating-point number.



</td>
</tr>
<tr>
<td valign="top">

public override Guid



</td>
<td valign="top">

 [GetGuid\(int\)](getguid-int-method-3c1688a.md) 



</td>
<td valign="top">

Returns the value of the specified column as a global unique identifier \(GUID\).



</td>
</tr>
<tr>
<td valign="top">

public override short



</td>
<td valign="top">

 [GetInt16\(int\)](getint16-int-method-3c16914.md) 



</td>
<td valign="top">

Returns the value of the specified column as a 16-bit signed integer.



</td>
</tr>
<tr>
<td valign="top">

public override int



</td>
<td valign="top">

 [GetInt32\(int\)](getint32-int-method-3c16992.md) 



</td>
<td valign="top">

Returns the value of the specified column as a 32-bit signed integer.



</td>
</tr>
<tr>
<td valign="top">

public override long



</td>
<td valign="top">

 [GetInt64\(int\)](getint64-int-method-3c16a13.md) 



</td>
<td valign="top">

Returns the value of the specified column as a 64-bit signed integer.



</td>
</tr>
<tr>
<td valign="top">

public override string



</td>
<td valign="top">

 [GetName\(int\)](getname-int-method-3c16aa6.md) 



</td>
<td valign="top">

Returns the name of the specified column.



</td>
</tr>
<tr>
<td valign="top">

public override int



</td>
<td valign="top">

 [GetOrdinal\(string\)](getordinal-string-method-3c16b3a.md) 



</td>
<td valign="top">

Returns the column ordinal, given the column name.



</td>
</tr>
<tr>
<td valign="top">

public override unsafe DataTable



</td>
<td valign="top">

 [GetSchemaTable\(\)](getschematable-method-3c16bb5.md) 



</td>
<td valign="top">

Returns a DataTable that describes the column metadata of the SADataReader.



</td>
</tr>
<tr>
<td valign="top">

public override string



</td>
<td valign="top">

 [GetString\(int\)](getstring-int-method-3c16c2f.md) 



</td>
<td valign="top">

Returns the value of the specified column as a string.



</td>
</tr>
<tr>
<td valign="top">

public TimeSpan



</td>
<td valign="top">

 [GetTimeSpan\(int\)](gettimespan-int-method-3c16cbd.md) 



</td>
<td valign="top">

Returns the value of the specified column as a TimeSpan object.



</td>
</tr>
<tr>
<td valign="top">

public ushort



</td>
<td valign="top">

 [GetUInt16\(int\)](getuint16-int-method-3c16d3a.md) 



</td>
<td valign="top">

Returns the value of the specified column as a 16-bit unsigned integer.



</td>
</tr>
<tr>
<td valign="top">

public uint



</td>
<td valign="top">

 [GetUInt32\(int\)](getuint32-int-method-3c16db5.md) 



</td>
<td valign="top">

Returns the value of the specified column as a 32-bit unsigned integer.



</td>
</tr>
<tr>
<td valign="top">

public ulong



</td>
<td valign="top">

 [GetUInt64\(int\)](getuint64-int-method-3c16e2e.md) 



</td>
<td valign="top">

Returns the value of the specified column as a 64-bit unsigned integer.



</td>
</tr>
<tr>
<td valign="top">

public override object



</td>
<td valign="top">

 [GetValue](getvalue-method-3c16fb2.md) 



</td>
<td valign="top">

Returns the value of the specified column as an Object.



</td>
</tr>
<tr>
<td valign="top">

public override unsafe int



</td>
<td valign="top">

 [GetValues\(object\[\]\)](getvalues-object-method-3c17032.md) 



</td>
<td valign="top">

Gets all the columns in the current row.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [IsDBNull\(int\)](isdbnull-int-method-3c171a9.md) 



</td>
<td valign="top">

Returns a value indicating whether the column contains NULL values.



</td>
</tr>
<tr>
<td valign="top">

public void



</td>
<td valign="top">

 [myDispose\(\)](mydispose-method-3c17327.md) 



</td>
<td valign="top">

Frees the resources associated with the object.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [NextResult\(\)](nextresult-method-3c173a5.md) 



</td>
<td valign="top">

Advances the SADataReader to the next result set when processing queries that return multiple result sets.



</td>
</tr>
<tr>
<td valign="top">

public override unsafe bool



</td>
<td valign="top">

 [Read\(\)](read-method-3c1741d.md) 



</td>
<td valign="top">

Reads the next row of the result set and moves the SADataReader to that row.



</td>
</tr>
</table>

 **Properties** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Property



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

public override int



</td>
<td valign="top">

 [Depth](depth-property-3c1608c.md) 



</td>
<td valign="top">

Gets a value indicating the depth of nesting for the current row.



</td>
</tr>
<tr>
<td valign="top">

public override int



</td>
<td valign="top">

 [FieldCount](fieldcount-property-3c1610b.md) 



</td>
<td valign="top">

Gets the number of columns in the result set.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [HasRows](hasrows-property-3c170aa.md) 



</td>
<td valign="top">

Gets a value that indicates whether the SADataReader contains one or more rows.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [IsClosed](isclosed-property-3c1712c.md) 



</td>
<td valign="top">

Gets a values that indicates whether the SADataReader is closed.



</td>
</tr>
<tr>
<td valign="top">

public override int



</td>
<td valign="top">

 [RecordsAffected](recordsaffected-property-3c174a0.md) 



</td>
<td valign="top">

The number of rows changed, inserted, or deleted by the execution of the SQL statement.



</td>
</tr>
<tr>
<td valign="top">

public override object



</td>
<td valign="top">

 [this](this-property-3c18144.md) 



</td>
<td valign="top">

Returns the value of a column in its native format.



</td>
</tr>
</table>



## Remarks

There is no constructor for SADataReader. To get an SADataReader object, execute an SACommand:

```
SACommand cmd = new SACommand(
   "SELECT EmployeeID FROM Employees", conn );
SADataReader reader = cmd.ExecuteReader();
```

You can only move forward through an SADataReader. If you need a more flexible object to manipulate results, then use an SADataAdapter.

The SADataReader retrieves rows as needed, whereas the SADataAdapter must retrieve all rows of a result set before you carry out any action on the object. For large result sets, this difference gives the SADataReader a much faster response time.

 *Implements:* IDataReader, IDisposable, IDataRecord, IListSource

For more information, see "Data access and manipulation".

**Related Information**  


[ExecuteReader\(\) Method](executereader-method-3c0f5ee.md "Executes a SQL statement that returns a result set.")

