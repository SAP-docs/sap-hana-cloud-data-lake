<!-- loio3bd9302d6c5f1014b5e6f54b85aed18a -->

# Data Alignment Requirements

When you use SQLBindCol, SQLBindParameter, or SQLGetData, a C data type is specified for the column or parameter.

On certain platforms, the storage \(memory\) provided for each column must be properly aligned to fetch or store a value of the specified type. The ODBC driver checks for proper data alignment. When an object is not properly aligned, the ODBC driver will issue an *"Invalid string or buffer length"* message \(*SQLSTATE* HY090 or S1090\).

The following table lists memory alignment requirements for processors such as Sun Sparc, Itanium-IA64, and ARM-based devices. The memory address of the data value must be a multiple of the indicated value.


<table>
<tr>
<th valign="top">

C Data Type



</th>
<th valign="top">

Alignment Required



</th>
</tr>
<tr>
<td valign="top">

SQL\_C\_CHAR



</td>
<td valign="top">

none



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_BINARY



</td>
<td valign="top">

none



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_GUID



</td>
<td valign="top">

none



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_BIT



</td>
<td valign="top">

none



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_STINYINT



</td>
<td valign="top">

none



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_UTINYINT



</td>
<td valign="top">

none



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_TINYINT



</td>
<td valign="top">

none



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_NUMERIC



</td>
<td valign="top">

none



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_DEFAULT



</td>
<td valign="top">

none



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_SSHORT



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_USHORT



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_SHORT



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_DATE



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_TIME



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_TIMESTAMP



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_TYPE\_DATE



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_TYPE\_TIME



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_TYPE\_TIMESTAMP



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_WCHAR



</td>
<td valign="top">

2 \(buffer size must be a multiple of 2 on all platforms\)



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_SLONG



</td>
<td valign="top">

4



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_ULONG



</td>
<td valign="top">

4



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_LONG



</td>
<td valign="top">

4



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_FLOAT



</td>
<td valign="top">

4



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_DOUBLE



</td>
<td valign="top">

8 \(4 for ARM\)



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_SBIGINT



</td>
<td valign="top">

8



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_UBIGINT



</td>
<td valign="top">

8



</td>
</tr>
</table>

The x86, x64, and PowerPC platforms do not require memory alignment. The x64 platform includes Advanced Micro Devices \(AMD\) AMD64 processors and Intel Extended Memory 64 Technology \(EM64T\) processors.

