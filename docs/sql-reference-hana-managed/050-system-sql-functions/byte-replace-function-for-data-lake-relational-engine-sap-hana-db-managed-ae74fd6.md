<!-- loioae74fd6f62dc4cd5b24408ce29a73fa3 -->

# BYTE\_REPLACE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Replaces a string with another string, and returns the new result.



```
BYTE_REPLACE( <source_string> , <search_string> , <replace_string> )
```



<a name="loioae74fd6f62dc4cd5b24408ce29a73fa3__section_q2z_l2l_srb"/>

## Parameters


<dl>
<dt><b>

 *<source\_string\>* 

</b></dt>
<dd>

The string to be searched.



</dd><dt><b>

 *<search\_string\>* 

</b></dt>
<dd>

The string to be searched for within *<source\_string\>* and replaced by *<replace\_string\>*. *<search\_string\>* is limited to 255 bytes. If *<search\_string\>* is an empty string, then *<source\_string\>* is returned unchanged.



</dd><dt><b>

 *<replace\_string\>* 

</b></dt>
<dd>

The string that replaces all instances of *<search\_string\>*. If *<replacement\_string\>* is an empty string, then all occurrences of *<search\_string\>* are deleted.



</dd>
</dl>



<a name="loioae74fd6f62dc4cd5b24408ce29a73fa3__section_bnl_m2l_srb"/>

## Returns

LONG BINARY



The following statement returns the binary value `0x78782e6465662e78782e676869`, which is the hexadecimal representation of the string `xx.def.xx.ghi`:

```
SELECT BYTE_REPLACE( 'abc.def.abc.ghi', 'abc', 'xx' );
```

**Related Information**  


[BYTE_REPLACE Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/4d5eb9fb4c7241bd97a13cc36f4caa1c.html "Replaces a string with another string, and returns the new result.") :arrow_upper_right:

