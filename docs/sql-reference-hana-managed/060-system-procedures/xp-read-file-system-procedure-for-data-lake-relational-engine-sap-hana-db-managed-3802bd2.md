<!-- loio3802bd2d3a464336b1abe16107b12e47 -->

# xp\_read\_file System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Reads a file and returns the contents of the file as a LONG BINARY variable.



<a name="loio3802bd2d3a464336b1abe16107b12e47__section_by2_t1x_fzb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

> ### Restriction:  
> This syntax cannot be run when connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_QUERY.



```
xp_read_file( <filename>[, <lazy> ] );
```



<a name="loio3802bd2d3a464336b1abe16107b12e47__section_mtf_kp2_srb"/>

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



<a name="loio3802bd2d3a464336b1abe16107b12e47__section_ups_kp2_srb"/>

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



<a name="loio3802bd2d3a464336b1abe16107b12e47__section_tp2_lp2_srb"/>

## Remarks

The function can be useful for inserting entire documents or images stored in files into tables. If the file cannot be read, the function returns NULL.

If the data file is in a different character set, you can use the CSCONVERT function to convert it.

You can also use the CSCONVERT function to address character set conversion requirements you have when using the xp\_read\_file system procedure.

If disk sandboxing is enabled, the file referenced in *<filename\>* must be in an accessible location.

The function returns NULL if the specified file does not exist.



<a name="loio3802bd2d3a464336b1abe16107b12e47__section_szs_mbb_1yb"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on the procedure
-   EXECUTE object-level privilege on the xp\_read\_real\_file procedure
-   READ FILE system privilege



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


[xp_read_file System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/3beb56b86c5f101495dbf54443bd191d.html "Reads a file and returns the contents of the file as a LONG BINARY variable.") :arrow_upper_right:

