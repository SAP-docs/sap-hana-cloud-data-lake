<!-- loio54ecc6f0577840c9b5a6f5cf440e1ffc -->

# getData\(Integer, Integer, Buffer, Integer, Integer\[, Function\]\) Method

Reads a stream of bytes from the specified LOB column, starting at the location indicated by dataOffset, into the buffer, starting at the location indicated by bufferOffset.



```
resultset.getData(colIndex, dataOffset, buffer, bufferOffset, length[, callback])
```



## Parameters


<table>
<tr>
<th valign="top">

Type



</th>
<th valign="top">

Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Integer



</td>
<td valign="top">

`colIndex`



</td>
<td valign="top">

The zero-based column index.



</td>
</tr>
<tr>
<td valign="top">

Integer



</td>
<td valign="top">

`dataOffset`



</td>
<td valign="top">

The index within the column where the read operation begins. For binary columns this value is in bytes. For string columns this value is in UTF-16 encoded characters.



</td>
</tr>
<tr>
<td valign="top">

Buffer



</td>
<td valign="top">

`buffer`



</td>
<td valign="top">

The buffer into which to copy the data.



</td>
</tr>
<tr>
<td valign="top">

Integer



</td>
<td valign="top">

`bufferOffset`



</td>
<td valign="top">

The index in bytes within the buffer to which the data is copied.



</td>
</tr>
<tr>
<td valign="top">

Integer



</td>
<td valign="top">

`length`



</td>
<td valign="top">

The maximum number of bytes to read.



</td>
</tr>
<tr>
<td valign="top">

Function



</td>
<td valign="top">

`callback`



</td>
<td valign="top">

The optional callback function.



</td>
</tr>
</table>



## Returns

Returns the actual number of bytes read.



## Remarks

This method can be synchronous or asynchronous. Specify a callback function to use this method asynchronously.

The callback function is of the following form:

```
function(err, result){
};
```

For string columns, the data filled into the buffer is UTF-8 encoded. The driver will not copy partial UTF-8 characters. Because of this, the number of bytes returned for a string column can be a few bytes less than the length parameter, even when there is more data available in the column.

Note that the `dataOffset` for the column is in UTF-16 units for strings, so non-BMP characters count as two UTF-16 units. The example below shows that Node.js string lengths are in UTF-16 units and can be used to compute the `dataOffset` parameter when getting multiple adjacent parts of column data:

> ### Sample Code:  
> ```
> var iq=require('@sap/iq-client');
> var client=iq.createConnection();
> client.connect({host=XXX-XXX.iq.hdl.trial-us10.hanacloud.ondemand.com:443;uid=XXXXXXX;pwd=XXXXXXXX;enc='TLS{tls_type=rsa;direct=yes}});
> // NCLOB_COL is of type NCLOB
> var stmt=client.prepare("SELECT TOP 1 NCLOB_COL FROM LOBTEST ORDER BY PK");
> var rs=stmt.execQuery();
> if(rs.next()) {
>     var buffer_size = 1000000;
>     var buffer = Buffer.alloc(buffer_size);
>     var offset = 0; // offset in UTF-16 character units into column
>     var total_bytes_read = 0;
>     while(true) {
>         var bytes_read = rs.getData(0, offset, buffer, 0, buffer_size);
>         if(bytes_read == 0) break;
>         var got_str = buffer.toString('utf8', 0, bytes_read);
>         console.log("getData got: " + bytes_read + " bytes");
>         console.log("  (" + got_str.length + " characters)"); // in UTF-16 units
>         console.log("  starting at: " + offset);
>         console.log("  first character retreived is: " + got_str[0]);
>         console.log("  last character retreived is:" + got_str[got_str.length-1]);
>         total_bytes_read += bytes_read;
>         offset += got_str.length;
>     }
>     console.log("Done getting data");
>     console.log("  total characters read is " + offset);
>     console.log("  total bytes read is " + total_bytes_read);
> }
> rs.close();
> stmt.drop();
> client.disconnect();
> ```

