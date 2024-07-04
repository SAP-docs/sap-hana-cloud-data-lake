<!-- loioa558efff84f210159092915333b9e6df -->

# INSERTSTR Function \[String\] for Data Lake Relational Engine

Inserts a string into another string at a specified position.



```
INSERTSTR ( <numeric-expression>, <string-expression1>, <string-expression2> );
```



<a name="loioa558efff84f210159092915333b9e6df__INSERTSTR_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The position after which *<string-expression2\>* is to be inserted. Use zero to insert a string at the beginning.



</dd><dt><b>

*<string-expression1\>*

</b></dt>
<dd>

The string into which *<string-expression2\>* is to be inserted.



</dd><dt><b>

*<string-expression2\>*

</b></dt>
<dd>

The string to be inserted.



</dd>
</dl>



<a name="loioa558efff84f210159092915333b9e6df__INSERTSTR_returns1"/>

## Result Set

LONG VARCHAR or LONG BINARY, depending on the data type of the input expressions.

> ### Note:  
> The result data type is a LONG VARCHAR. If you use `INSERTSTR` in a `SELECT INTO` statement, you must use `CAST` and set `INSERTSTR` to the correct data type and size.



<a name="loioa558efff84f210159092915333b9e6df__INSERTSTR_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar.



<a name="loioa558efff84f210159092915333b9e6df__INSERTSTR_example1"/>

## Examples

The following statement returns the value "backoffice":

```
SELECT INSERTSTR( 0, 'office ', 'back' ) FROM iq_dummy;
```

**Related Information**  


[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[STUFF Function \[String\] for Data Lake Relational Engine](stuff-function-string-for-data-lake-relational-engine-a58705b.md "Deletes a number of characters from one string and replaces them with another string.")

[INSERTSTR Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/064a64ca374142608c2c968248d9bbe7.html "Inserts a string into another string at a specified position.") :arrow_upper_right:

