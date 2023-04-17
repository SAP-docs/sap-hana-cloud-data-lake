<!-- loio80456cf5652446c4b1279d5fb21e21dd -->

# DAYS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the number of days since an arbitrary starting date, returns the number of days between two specified dates, or adds the specified *<integer-expression\>* number of days to a given date.



```
DAYS ( <datetime-expression> )
  | ( <datetime-expression>, <datetime-expression> )
  | ( <datetime-expression>, <integer-expression> )
```



<a name="loio80456cf5652446c4b1279d5fb21e21dd__section_vqz_z1m_srb"/>

## Parameters

 *<datetime-expression\>*
 :   A date and time.

  *<integer-expression\>*
 :   The number of days to be added to the *<datetime-expression\>*. If the *<integer-expression\>* is negative, the appropriate number of days are subtracted from the date and time. If you supply an integer expression, the *<datetime-expression\>* must be explicitly cast as a date.

 

<a name="loio80456cf5652446c4b1279d5fb21e21dd__section_eqm_1bm_srb"/>

## Returns

INT when you specify two datetime expressions.

TIMESTAMP when the second argument you specify is an integer.



<a name="loio80456cf5652446c4b1279d5fb21e21dd__section_e1c_bbm_srb"/>

## Remarks

`DAYS` ignores hours, minutes, and seconds.



<a name="loio80456cf5652446c4b1279d5fb21e21dd__section_a1l_bbm_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio80456cf5652446c4b1279d5fb21e21dd__section_hcy_sl3_wrb"/>

## Examples

-   The following statement returns the integer value 729948:

    ```
    SELECT DAYS( '1998-07-13 06:07:12' ) FROM iq_dummy
    ```

-   The following statement returns the integer value -366, which is the difference between the two dates:

    ```
    SELECT DAYS( '1998-07-13 06:07:12',
    '1997-07-12 10:07:12' ) FROM iq_dummy
    ```

-   The following statement returns the value 1999-07-14:

    ```
    SELECT DAYS( CAST('1998-07-13' AS DATE ), 366 )
    FROM iq_dummy
    ```


**Related Information**  


[DAYS Function [Date and Time] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a54a45b584f21015a4c2ab2c117fc738.html "Returns the number of days since an arbitrary starting date, returns the number of days between two specified dates, or adds the specified integer-expression number of days to a given date.") :arrow_upper_right:

