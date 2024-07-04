<!-- loio65d438896f2948c4afb37190924dbf7e -->

# BYTE\_LOCATE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the position of one BYTE string within another.



```
BYTE_LOCATE( <source_string> , <search_string> [ , <start_position> ] );
```



<a name="loio65d438896f2948c4afb37190924dbf7e__section_m2v_v2l_srb"/>

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

The string to be searched for within *<source\_string\>*.



</dd><dt><b>

*<start\_position\>* 

</b></dt>
<dd>

The byte position in the string to begin the search. The first byte is position 1. If the starting offset is negative, then the BYTE\_LOCATE function returns the last matching string offset rather than the first, as counted from the end of the string. A negative offset indicates how much of the end of the string is to be excluded from the search. The number of bytes excluded is calculated as `(-1 * offset) -1`.

Although *<start\_position\>* acts as an offset for where the search is started, the return value still reflects the actual starting position of the matching string, regardless of where the search was started.



</dd>
</dl>



<a name="loio65d438896f2948c4afb37190924dbf7e__section_uch_w2l_srb"/>

## Result Set

INTEGER



## Example

When *<start\_position\>* is any positive number from 0 to 8 inclusive, the following statement returns 8, indicating that the first matching byte in the string is at position 8. If *<start\_position\>* is greater than 8, then the example returns 0 because the string 'party' isn’t found after position 8.

```
SELECT BYTE_LOCATE(
   'office party this week - rsvp as soon as possible',
   'party',
   2 );
```

When *<start\_position\>* is any number from 0 to -38 inclusive, the following statement returns 8. Any number lower than -38 returns 0. This indicates that the first matching byte in the string is at position 8, and indicates that the position of the last matching byte \(the 'y' in 'party'\) is in position 38 as counted backwards from the end of the string.

```
SELECT BYTE_LOCATE(
   'office party this week - rsvp as soon as possible',
   'party',
   -38 );
```

**Related Information**  


[BYTE_LOCATE Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/6b6d91ad148841f781fb65d0a68a8b82.html "Returns the position of one BYTE string within another.") :arrow_upper_right:

