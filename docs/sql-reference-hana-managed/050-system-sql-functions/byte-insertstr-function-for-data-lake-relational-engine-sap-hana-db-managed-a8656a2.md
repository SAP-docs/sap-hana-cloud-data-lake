<!-- loioa8656a236f5a4afdb003988d8f040939 -->

# BYTE\_INSERTSTR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Inserts a string into another string at a position specified in bytes.



```
BYTE_INSERTSTR( <insert_position> , <source_string> , <insert_string> )
```



<a name="loioa8656a236f5a4afdb003988d8f040939__section_x2t_3gl_srb"/>

## Parameters

  *<insert\_position\>* 
 :   The byte position after which *<insert\_string\>* is to be inserted. The first byte in the string is position 1. Use 0 to insert before the first byte in the string.

   *<source\_string\>* 
 :   The string into which *<insert\_string\>* is to be inserted. *<source\_string\>* can be any length.

   *<insert\_string\>* 
 :   The string to be inserted.

 

<a name="loioa8656a236f5a4afdb003988d8f040939__section_mm2_jgl_srb"/>

## Returns

LONG BINARY

**Related Information**  


[BYTE_INSERTSTR Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/81f411c06ce21014834ca45160d818e3.html "Inserts a string into another string at a position specified in bytes.") :arrow_upper_right:

