<!-- loio0eaddd0e507e47f397ef96f11b3d3868 -->

# READ\_SERVER\_FILE Function \[String\] for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Reads data from the specified file on the server and returns the full or partial contents of the file as a LONG BINARY value.



```
READ_SERVER_FILE( <filename> [ , <start> [ , <length> ] ] )
```



## Parameters

  *<filename\>* 
 :   LONG VARCHAR value indicating the path and name of the file

    For diagnostic files, *<filename\>* requires the common prefix:

    -   <code>/diag/logs/<i class="varname">&lt;subdirectory/&gt;</i><i class="varname">&lt;filename&gt;</i></code> for diagnostic logs

    -   <code>/diag/audit/<i class="varname">&lt;filename&gt;</i></code> for auditing \(ETD\) files


   *<start\>* 
 :   The start position of the file to read, in bytes. The first byte in the file is at position 1. A negative starting position specifies the number of bytes from the end of the file rather than from the beginning.

    -   If *<start\>* is not specified, a value of 1 is used.
    -   If *<start\>* is zero and *<length\>* is non-negative, a value of 1 is used.
    -   If *<start\>* is zero and *<length\>* is negative, a value of -1 is used.

   *<length\>* 
 :   The length of the file to read, in bytes.

    -   If *<length\>* is not specified, the function reads from the starting position to the end of the file.
    -   If *<length\>* is positive, the function reads at most *<length\>* bytes beginning at the starting position.
    -   If *<length\>* is negative, the function returns at most *<length\>* ending at the starting position.

 

## Returns

LONG BINARY



## Remarks

This function returns the full or partial \(if *<start\>* and/or *<length\>* are specified\) contents of the named file as a LONG BINARY value. If the file doesn’t exist or cannot be read, NULL is returned.

The READ\_SERVER\_FILE function supports reading files larger than 2GB. However, the returned content is limited to 2GB. If the returned content exceeds this limit, a SQL error is returned.

If the data file is in a different character set, you can use the CSCONVERT function to convert it. You can also use the CSCONVERT function to address the character set conversion requirements you may have when using the READ\_SERVER\_FILE server function.

If disk sandboxing is enabled, the file referenced in *<filename\>* must be in an accessible location.



## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 

```
SELECT read_server_file('/diag/logs/mpx-writer-0-0/iqaas_20211217_110352.331_mpx-coord-0.iqmsg')
```

**Related Information**  


[READ_SERVER_FILE Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/81fb732a6ce21014b442b1082d0be5af.html "Reads data from the specified file on the server and returns the full or partial contents of the file as a LONG BINARY value.") :arrow_upper_right:

