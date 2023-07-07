<!-- loio3802bd2d3a464336b1abe16107b12e47 -->

# xp\_read\_file System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Reads a file and returns the contents of the file as a LONG BINARY variable.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Running Procedures](remote-execute-usage-examples-for-running-procedures-3e7f86d.md) for more information.



```
xp_read_file(
<filename>
[, <lazy> ]
)
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

## Returns

This function returns the contents of the named file as a LONG BINARY value. If the file does not exist or cannot be read, NULL is returned.



<a name="loio3802bd2d3a464336b1abe16107b12e47__section_tp2_lp2_srb"/>

## Remarks

The function can be useful for inserting entire documents or images stored in files into tables. If the file cannot be read, the function returns NULL.

If the data file is in a different character set, you can use the CSCONVERT function to convert it.

You can also use the CSCONVERT function to address character set conversion requirements you have when using the xp\_read\_file system procedure.

If disk sandboxing is enabled, the file referenced in *<filename\>* must be in an accessible location.

The function returns NULL if the specified file does not exist.



## Privileges

You need all of the following:

-   EXECUTE object-level privilege on the system procedure
-   EXECUTE privilege on the xp\_read\_real\_file system procedure
-   READ FILE system privilege



```
SELECT xp_read_file('/diag/logs/mpx-writer-0-0/mpx-writer-0-0/iqaas_20211217_110352.332_mpx-coord-0.iqmsg')
```

