<!-- loio538f342383bd4520a088b814fc76ac65 -->

# BYTE\_STUFF Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Deletes multiple bytes from one string and replaces them with different bytes.



```
BYTE_STUFF( <source_string> , <start_position> , <length> , <insert_string> );
```



<a name="loio538f342383bd4520a088b814fc76ac65__section_dfl_1dl_srb"/>

## Parameters


<dl>
<dt><b>

*<source\_string\>* 

</b></dt>
<dd>

The byte string to be modified by the BYTE\_STUFF function. *<source\_string\>* can be any length.



</dd><dt><b>

*<start\_position\>* 

</b></dt>
<dd>

The byte position at which to begin deleting bytes. The first byte in the string is position 1.



</dd><dt><b>

*<length\>* 

</b></dt>
<dd>

The number of bytes to delete.



</dd><dt><b>

*<insert\_string\>* 

</b></dt>
<dd>

The string to be inserted. To delete a portion of a string using the BYTE\_STUFF function, use a NULL replacement string.



</dd>
</dl>



<a name="loio538f342383bd4520a088b814fc76ac65__section_brx_1dl_srb"/>

## Result Set

LONG BINARY



## Example

The following statement inserts the hexadecimal string 123456 starting at the sixth byte position, and returns the binary value `0xfedcba9876123456543210`:

```
SELECT BYTE_STUFF(0xfedcba9876543210, 6, 0, 0x123456);
```

**Related Information**  


[BYTE_STUFF Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/81f4257b6ce21014b495a59f54e5e617.html "Deletes multiple bytes from one string and replaces them with different bytes.") :arrow_upper_right:

