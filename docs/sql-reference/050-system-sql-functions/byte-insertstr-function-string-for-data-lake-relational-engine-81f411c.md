<!-- loio81f411c06ce21014834ca45160d818e3 -->

# BYTE\_INSERTSTR Function \[String\] for Data Lake Relational Engine

Inserts a string into another string at a position specified in bytes.



```
BYTE_INSERTSTR( <insert_position> , <source_string> , <insert_string> );
```



<a name="loio81f411c06ce21014834ca45160d818e3__BYTE_INSERTSTR_parm1"/>

## Parameters


<dl>
<dt><b>

*<insert\_position\>* 

</b></dt>
<dd>

The byte position after which *<insert\_string\>* is to be inserted. The first byte in the string is position 1. Use 0 to insert before the first byte in the string.



</dd><dt><b>

*<source\_string\>* 

</b></dt>
<dd>

The string into which *<insert\_string\>* is to be inserted. *<source\_string\>* can be any length.



</dd><dt><b>

*<insert\_string\>* 

</b></dt>
<dd>

The string to be inserted.



</dd>
</dl>



<a name="loio81f411c06ce21014834ca45160d818e3__BYTE_INSERTSTR_returns1"/>

## Result Set

LONG BINARY

**Related Information**  


[BYTE_INSERTSTR Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/a8656a236f5a4afdb003988d8f040939.html "Inserts a string into another string at a position specified in bytes.") :arrow_upper_right:

