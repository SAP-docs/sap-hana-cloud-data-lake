<!-- loio3bd947836c5f10149f36c98b9670da4a -->

# ODBC Applications on Windows

When linking your application, you must link against the appropriate import library file to have access to the ODBC functions.

The import library defines entry points for the ODBC driver manager `odbc32.dll`. The driver manager in turn loads the ODBC driver <code>dbodbc<i>17</i>.dll</code>.

Typically, the import library is stored under the `Lib` directory structure of the Microsoft platform SDK:


<table>
<tr>
<th valign="top">

Operating System



</th>
<th valign="top">

Import Library



</th>
</tr>
<tr>
<td valign="top">

Windows \(32-bit\)



</td>
<td valign="top">

 `Lib\odbc32.lib` 



</td>
</tr>
<tr>
<td valign="top">

Windows \(64-bit\)



</td>
<td valign="top">

 `Lib\x64\odbc32.lib` 



</td>
</tr>
</table>

