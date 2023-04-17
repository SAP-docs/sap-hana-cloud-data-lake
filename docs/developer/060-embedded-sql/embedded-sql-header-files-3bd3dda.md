<!-- loio3bd3dda56c5f10148997deb09068a4ad -->

# Embedded SQL Header Files

All header files are installed in the `SDK\Include` subdirectory of your software installation directory.




<table>
<tr>
<th valign="top">

File Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `sqlca.h` 



</td>
<td valign="top">

Main header file included in all Embedded SQL programs. This file includes the structure definition for the SQL Communication Area \(SQLCA\) and prototypes for all Embedded SQL database interface functions.



</td>
</tr>
<tr>
<td valign="top">

 `sqlda.h` 



</td>
<td valign="top">

SQL Descriptor Area structure definition included in Embedded SQL programs that use dynamic SQL.



</td>
</tr>
<tr>
<td valign="top">

 `sqldef.h` 



</td>
<td valign="top">

Definition of Embedded SQL interface data types. This file also contains structure definitions and return codes needed for starting the database server from a C program.



</td>
</tr>
<tr>
<td valign="top">

 `sqlerr.h` 



</td>
<td valign="top">

Definitions for error codes returned in the sqlcode field of the SQLCA.



</td>
</tr>
<tr>
<td valign="top">

 `sqlstate.h` 



</td>
<td valign="top">

Definitions for ANSI/ISO SQL standard error states returned in the sqlstate field of the SQLCA.



</td>
</tr>
<tr>
<td valign="top">

 `pshpk1.h, pshpk4.h, poppk.h` 



</td>
<td valign="top">

These headers ensure that structure packing is handled correctly.



</td>
</tr>
</table>

