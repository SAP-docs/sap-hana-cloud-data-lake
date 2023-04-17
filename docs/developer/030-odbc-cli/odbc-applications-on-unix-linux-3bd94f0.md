<!-- loio3bd94f056c5f101483ea8e3a49ce5469 -->

# ODBC Applications on UNIX/Linux

An ODBC driver manager for UNIX and Linux is included with the database server software and there are third party driver managers available. The following information describes how to build ODBC applications that do not use an ODBC driver manager.



## ODBC Driver

The ODBC driver is a shared object or shared library. Separate versions of the ODBC driver are supplied for single-threaded and multithreaded applications. A generic ODBC driver is supplied that will detect the threading model in use and direct calls to the appropriate single-threaded or multithreaded library.

The ODBC drivers are the following files:


<table>
<tr>
<th valign="top">

Operating System



</th>
<th valign="top">

Threading Model



</th>
<th valign="top">

ODBC Driver



</th>
</tr>
<tr>
<td valign="top">

\(all UNIX/Linux except HP-UX\)



</td>
<td valign="top">

Generic



</td>
<td valign="top">

 <code>libdbodbc<i>17</i>.so (libdbodbc<i>17</i>.so.1)</code> 



</td>
</tr>
<tr>
<td valign="top">

\(all UNIX/Linux except HP-UX\)



</td>
<td valign="top">

Single threaded



</td>
<td valign="top">

 <code>libdbodbc<i>17</i>_n.so (libdbodbc<i>17</i>_n.so.1)</code> 



</td>
</tr>
<tr>
<td valign="top">

\(all UNIX/Linux except HP-UX\)



</td>
<td valign="top">

Multithreaded



</td>
<td valign="top">

 <code>libdbodbc<i>17</i>_r.so (libdbodbc<i>17</i>_r.so.1)</code> 



</td>
</tr>
</table>

The libraries are installed as symbolic links to the shared library with a version number \(shown in parentheses\).

When linking an ODBC application on UNIX or Linux, link your application against the generic ODBC driver <code>libdbodbc<i>17</i></code>. When deploying your application, ensure that the appropriate \(or all\) ODBC driver versions \(non-threaded or threaded\) are available in the user's library path.



## Data Source Information

If the presence of an ODBC driver manager is not detected, the ODBC driver uses the system information file for data source information.

