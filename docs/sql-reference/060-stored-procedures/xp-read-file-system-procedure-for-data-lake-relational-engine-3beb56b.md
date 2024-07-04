<!-- loio3beb56b86c5f101495dbf54443bd191d -->

# xp\_read\_file System Procedure for Data Lake Relational Engine

Reads a file and returns the contents of the file as a LONG BINARY variable.



<a name="loio3beb56b86c5f101495dbf54443bd191d__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
xp_read_file( <filename>[, <lazy> ] )
```



<a name="loio3beb56b86c5f101495dbf54443bd191d__xp_read_file_parm1"/>

## Parameters


<dl>
<dt><b>

*<filename\>* 

</b></dt>
<dd>

Use this LONG VARCHAR parameter to specify the name of the file for which to return the contents.



</dd><dt><b>

*<lazy\>* 

</b></dt>
<dd>

When you specify this optional INTEGER parameter and its value is not 0, the contents of the file are not read until they are requested. Reads only occur when the LONG BINARY value is accessed and only on the portion of the file that is requested. The default is 0, or non-lazy.



</dd>
</dl>



<a name="loio3beb56b86c5f101495dbf54443bd191d__xp_read_file_returns1"/>

## Result Set

This function returns the contents of the named file as a LONG BINARY value. If the file does not exist or cannot be read, NULL is returned.


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*<filename\>*

</td>
<td valign="top">

Displays NULL if the filename does not exist or cannot be read.

</td>
</tr>
</table>



<a name="loio3beb56b86c5f101495dbf54443bd191d__xp_read_file_remarks1"/>

## Remarks

The function can be useful for inserting entire documents or images stored in files into tables. If the file cannot be read, the function returns NULL.

If the data file is in a different character set, you can use the CSCONVERT function to convert it.

You can also use the CSCONVERT function to address character set conversion requirements you have when using the xp\_read\_file system procedure.

If disk sandboxing is enabled, the file referenced in *<filename\>* must be in an accessible location.

The function returns NULL if the specified file does not exist.



<a name="loio3beb56b86c5f101495dbf54443bd191d__xp_read_file_priv1"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   READ FILE system privilege



<a name="loio3beb56b86c5f101495dbf54443bd191d__xp_read_file_example1"/>

## Examples

This example indicates that filename mpx-coord-0.iqmsg in path /diag/logs/ either does not exist or cannot be read.

```
Call xp_read_file('/diag/logs/mpx-coord-0.iqmsg');
```


<table>
<tr>
<th valign="top">

xp\_read\_file\('/diag/logs/mpx-coord-0.iqmsg'\)

</th>
</tr>
<tr>
<td valign="top">

NULL

</td>
</tr>
</table>

**Related Information**  


[xp_read_file System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/3802bd2d3a464336b1abe16107b12e47.html "Reads a file and returns the contents of the file as a LONG BINARY variable.") :arrow_upper_right:

[xp_sprintf System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/bcaf180e679e43d78733830fb7e4c2fa.html "Builds a result string from a set of input strings.") :arrow_upper_right:

