<!-- loio3bd3415f6c5f10148b21ce0c1b4c08b4 -->

# Summary of Indicator Variable Values

Indicator values are used to convey information about retrieved column values.

The following table provides a summary of indicator variable usage.


<table>
<tr>
<th valign="top">

Indicator Value



</th>
<th valign="top">

Supplying Value to Database



</th>
<th valign="top">

Receiving Value from Database



</th>
</tr>
<tr>
<td valign="top">

\> 0



</td>
<td valign="top">

Host variable value



</td>
<td valign="top">

Retrieved value was truncated \(actual length in indicator variable\).



</td>
</tr>
<tr>
<td valign="top">

0



</td>
<td valign="top">

Host variable value



</td>
<td valign="top">

Fetch successful, or conversion\_error set to On.



</td>
</tr>
<tr>
<td valign="top">

\-1



</td>
<td valign="top">

NULL value



</td>
<td valign="top">

NULL result.



</td>
</tr>
<tr>
<td valign="top">

\-2



</td>
<td valign="top">

NULL value



</td>
<td valign="top">

Conversion error \(when conversion\_error is set to Off only\). SQLCODE indicates a CANNOT\_CONVERT warning.



</td>
</tr>
<tr>
<td valign="top">

< -2



</td>
<td valign="top">

NULL value



</td>
<td valign="top">

NULL result.



</td>
</tr>
</table>

