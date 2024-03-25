<!-- loioa579952184f210159e17940c17a6d8f7 -->

# REPLACE Function \[String\] for Data Lake Relational Engine

Replaces all occurrences of a substring with another substring.



```
REPLACE ( <original-string>, <search-string>, <replace-string> );
```



<a name="loioa579952184f210159e17940c17a6d8f7__REPLACE_parm1"/>

## Parameters

If any argument is NULL, the function returns NULL.


<dl>
<dt><b>

*<original-string\>*

</b></dt>
<dd>

The string to be searched. This string can be any length.



</dd><dt><b>

*<search-string\>*

</b></dt>
<dd>

The string to be searched for and replaced with *<replace-string\>*. This string is limited to 255 bytes. If *<search-string\>* is an empty string, the original string is returned unchanged.



</dd><dt><b>

*<replace-string\>*

</b></dt>
<dd>

The replacement string, which replaces *<search-string\>*. This can be any length. If *<replace-string\>* is an empty string, all occurrences of *<search-string\>* are deleted.



</dd>
</dl>



<a name="loioa579952184f210159e17940c17a6d8f7__REPLACE_returns1"/>

## Result Set

-   LONG BINARY

-   LONG VARCHAR

-   LONG NVARCHAR


> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `REPLACE` in a `SELECT INTO` statement, you must use `CAST` and set `REPLACE` to the correct data type and size.



<a name="loioa579952184f210159e17940c17a6d8f7__REPLACE_remarks1"/>

## Remarks

The result data type of a `REPLACE` function is a `LONG VARCHAR`. If you use `REPLACE` in a `SELECT INTO` statement, you must use `CAST` and set `REPLACE` to the correct data type and size.

If all arguments are of binary data type, the `REPLACE` function behaves the same as the `BYTE_REPLACE` function.

There are two ways to work around this issue:

-   Declare a local temporary table, then perform an `INSERT`:

    ```
    DECLARE local temporary table #mytable 
      (name_column char(10)) on commit preserve rows;
    INSERT INTO #mytable SELECT REPLACE(name,'0','1')   FROM dummy_table01;
    ```

-   Use `CAST`:

    ```
    SELECT CAST(replace(name, '0', '1') AS Char(10)) into #mytable from dummy_table01;
    ```


If you need to control the width of the resulting column when *<replace-string\>* is wider than *<search-string\>*, use the `CAST` function. For example:

```
CREATE TABLE aa(a CHAR(5));
INSERT INTO aa VALUES('CCCCC');
COMMIT;
SELECT a, CAST(REPLACE(a,'C','ZZ') AS CHAR(5)) FROM aa;
```



<a name="loioa579952184f210159e17940c17a6d8f7__REPLACE_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioa579952184f210159e17940c17a6d8f7__REPLACE_examples1"/>

## Examples

-   The following statement returns the value "xx.def.xx.ghi":

    ```
    SELECT REPLACE( 'abc.def.abc.ghi', 'abc', 'xx' ) FROM iq_dummy;
    ```

-   The following statement generates a result set containing `ALTER PROCEDURE` statements, which when executed, repair stored procedures that reference a table that has been renamed \(to be useful, the table name must be unique\):

    ```
    SELECT REPLACE(
      replace(proc_defn,'OldTableName','NewTableName'),
      'create procedure',
      'alter procedure')
    FROM SYS.SYSPROCEDURE
    WHERE proc_defn LIKE '%OldTableName%';
    ```

-   Use a separator other than the comma for the `LIST` function:

    ```
    SELECT REPLACE( list( table_id ), ',', '--')
    FROM  SYS.ISYSTAB
    WHERE table_id <= 5;
    ```


**Related Information**  


[REPEAT Function \[String\] for Data Lake Relational Engine](repeat-function-string-for-data-lake-relational-engine-a579104.md "Concatenates a string a specified number of times.")

[REPLICATE Function \[String\] for Data Lake Relational Engine](replicate-function-string-for-data-lake-relational-engine-a57a156.md "Concatenates a string a specified number of times.")

[INSERTSTR Function \[String\] for Data Lake Relational Engine](insertstr-function-string-for-data-lake-relational-engine-a558eff.md "Inserts a string into another string at a specified position.")

[STUFF Function \[String\] for Data Lake Relational Engine](stuff-function-string-for-data-lake-relational-engine-a58705b.md "Deletes a number of characters from one string and replaces them with another string.")

[AES\_DECRYPT Function \[String\] for Data Lake Relational Engine](aes-decrypt-function-string-for-data-lake-relational-engine-a4c35f4.md "Decrypts the string using the supplied key, and returns, by default, a VARBINARY or LONG BINARY, or the original plaintext type.")

[AES\_ENCRYPT Function \[String\] for Data Lake Relational Engine](aes-encrypt-function-string-for-data-lake-relational-engine-a4c3260.md "Encrypts the specified values using the supplied encryption key, and returns a VARBINARY or LONG VARBINARY.")

[CAST Function \[Data Type Conversion\] for Data Lake Relational Engine](cast-function-data-type-conversion-for-data-lake-relational-engine-a53996d.md "Returns the value of an expression converted to a supplied data type.")

[CONVERT Function \[Data Type Conversion\] for Data Lake Relational Engine](convert-function-data-type-conversion-for-data-lake-relational-engine-a53f6ef.md "Returns an expression converted to a supplied data type.")

[HOURS Function \[Date and Time\] for Data Lake Relational Engine](hours-function-date-and-time-for-data-lake-relational-engine-a556e14.md "Returns the number of hours since an arbitrary starting date and time, the number of whole hours between two specified times, or adds the specified integer-expression number of hours to a time.")

[MINUTES Function \[Date and Time\] for Data Lake Relational Engine](minutes-function-date-and-time-for-data-lake-relational-engine-a5648d4.md "Returns the number of minutes since an arbitrary date and time, the number of whole minutes between two specified times, or adds the specified integer-expression number of minutes to a time.")

[MONTHS Function \[Date and Time\] for Data Lake Relational Engine](months-function-date-and-time-for-data-lake-relational-engine-a566ced.md "Returns the number of months since an arbitrary starting date/time or the number of months between two specified date/times, or adds the specified integer-expression number of months to a date/time.")

[SECOND Function \[Date and Time\] for Data Lake Relational Engine](second-function-date-and-time-for-data-lake-relational-engine-a57dc03.md "Returns a number from 0 to 59 corresponding to the second component of the given date/time value.")

[WEEKS Function \[Date and Time\] for Data Lake Relational Engine](weeks-function-date-and-time-for-data-lake-relational-engine-a590601.md "Returns the number of weeks since an arbitrary starting date/time, returns the number of weeks between two specified date/times, or adds the specified integer-expression number of weeks to a date/time.")

[YEAR Function \[Date and Time\] for Data Lake Relational Engine](year-function-date-and-time-for-data-lake-relational-engine-a591eb9.md "Returns a 4-digit number corresponding to the year of the given date/time.")

[YEARS Function \[Date and Time\] for Data Lake Relational Engine](years-function-date-and-time-for-data-lake-relational-engine-a5926bf.md "Returns a 4-digit number corresponding to the year of a given date/time, returns the number of years between two specified date/times, or adds the specified integer-expression number of years to a date/time.")

[LCASE Function \[String\] for Data Lake Relational Engine](lcase-function-string-for-data-lake-relational-engine-a55c82d.md "Converts all characters in a string to lowercase.")

[LEFT Function \[String\] for Data Lake Relational Engine](left-function-string-for-data-lake-relational-engine-a55d883.md "Returns a specified number of characters from the beginning of a string.")

[LOWER Function \[String\] for Data Lake Relational Engine](lower-function-string-for-data-lake-relational-engine-a561324.md "Converts all characters in a string to lowercase.")

[REVERSE Function \[String\] for Data Lake Relational Engine](reverse-function-string-for-data-lake-relational-engine-a57a972.md "Takes one argument as an input of type BINARY or STRING and returns the specified string with characters listed in reverse order.")

[RIGHT Function \[String\] for Data Lake Relational Engine](right-function-string-for-data-lake-relational-engine-a57b364.md "Returns the rightmost characters of a string.")

[UCASE Function \[String\] for Data Lake Relational Engine](ucase-function-string-for-data-lake-relational-engine-a58c382.md "Converts all characters in a string to uppercase.")

[UPPER Function \[String\] for Data Lake Relational Engine](upper-function-string-for-data-lake-relational-engine-a58cbc0.md "Converts all characters in a string to uppercase.")

[REPLACE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/b8f3ed4beb9645e98dee8a2c50011263.html "Replaces all occurrences of a substring with another substring.") :arrow_upper_right:

