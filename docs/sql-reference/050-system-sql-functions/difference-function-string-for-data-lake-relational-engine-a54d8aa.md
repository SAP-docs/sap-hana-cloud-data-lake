<!-- loioa54d8aac84f210158ef283ad984de764 -->

# DIFFERENCE Function \[String\] for Data Lake Relational Engine

Compares two strings, evaluates the similarity between them, and returns a value from 0 to 4.



```
DIFFERENCE ( <string-expression1>, <string-expression2> );
```



<a name="loioa54d8aac84f210158ef283ad984de764__DIFFERENCE_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression1\>*

</b></dt>
<dd>

The first string to compare.



</dd><dt><b>

*<string-expression2\>*

</b></dt>
<dd>

The second string to compare.



</dd>
</dl>



<a name="loioa54d8aac84f210158ef283ad984de764__DIFFERENCE_returns1"/>

## Result Set

SMALLINT



<a name="loioa54d8aac84f210158ef283ad984de764__DIFFERENCE_remarks1"/>

## Remarks

The best match is 4.



<a name="loioa54d8aac84f210158ef283ad984de764__DIFFERENCE_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa54d8aac84f210158ef283ad984de764__DIFFERENCE_examples1"/>

## Examples

-   The following statement returns the value 4:

    ```
    SELECT DIFFERENCE( 'Smith', 'Smith' ) FROM iq_dummy;
    ```

-   The following statement returns the value 4:

    ```
    SELECT DIFFERENCE( 'Smith', 'Smyth' ) FROM iq_dummy;
    ```

-   The following statement returns the value 3:

    ```
    SELECT DIFFERENCE( 'Smith', 'Sweeney' ) FROM iq_dummy;
    ```

-   The following statement returns the value 2:

    ```
    SELECT DIFFERENCE( 'Smith', 'Jones' ) FROM iq_dummy;
    ```

-   The following statement returns the value 1:

    ```
    SELECT DIFFERENCE( 'Smith', 'Rubin' ) FROM iq_dummy;
    ```

-   The following statement returns the value 0:

    ```
    SELECT DIFFERENCE( 'Smith', 'Wilkins' ) FROM iq_dummy;
    ```


**Related Information**  


[SOUNDEX Function \[String\] for Data Lake Relational Engine](soundex-function-string-for-data-lake-relational-engine-a580dde.md "Returns a number representing the sound of a string.")

[DATE\_FIRST\_DAY\_OF\_WEEK Option for Data Lake Relational Engine](../090-database-options/date-first-day-of-week-option-for-data-lake-relational-engine-a632279.md "Determines the first day of the week.")

[DIFFERENCE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/3b8bafe468ce4160b52b7b25a5de50a0.html "Compares two strings, evaluates the similarity between them, and returns a value from 0 to 4.") :arrow_upper_right:

