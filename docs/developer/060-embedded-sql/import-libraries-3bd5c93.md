<!-- loio3bd5c9386c5f1014b8ec9653b1eabac7 -->

# Import Libraries

Import libraries are installed in subdirectories of your software installation directory.



On UNIX and Linux platforms, all import libraries are installed in the `lib32` and `lib64` subdirectories, under the software installation directory.


<table>
<tr>
<th valign="top">

Operating System



</th>
<th valign="top">

Compiler



</th>
<th valign="top">

Import Library



</th>
</tr>
<tr>
<td valign="top">

Linux \(unthreaded applications\)



</td>
<td valign="top">

All compilers



</td>
<td valign="top">

 <code>libdblib<i>17</i>.so</code>, <code>libdbtasks<i>17</i>.so</code>, <code>libdblib<i>17</i>.sl</code>, <code>libdbtasks<i>17</i>.sl</code> 



</td>
</tr>
<tr>
<td valign="top">

Linux \(threaded applications\)



</td>
<td valign="top">

All compilers



</td>
<td valign="top">

 <code>libdblib<i>17</i>_r.so</code>, <code>libdbtasks<i>17</i>_r.so</code>,<code>libdblib<i>17</i>_r.sl</code>, <code>libdbtasks<i>17</i>_r.sl</code> 



</td>
</tr>
</table>

The <code>libdbtasks<i>17</i></code> libraries are called by the <code>libdblib<i>17</i></code> libraries. Some compilers locate <code>libdbtasks<i>17</i></code> automatically. For others, you must specify it explicitly.

