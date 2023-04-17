<!-- loio0cf8ed274a1d4591baedd1691a352a48 -->

# YMD Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a date value corresponding to the given year, month, and day of the month.



```
YMD ( <integer-expression1>, <integer-expression2>, <integer-expression3> )
```



<a name="loio0cf8ed274a1d4591baedd1691a352a48__section_yq2_wbv_vrb"/>

## Parameters

 *<integer-expression1\>*
 :   The year.

  *<integer-expression2\>*
 :   The number of the month. If the month is outside the range 1–12, the year is adjusted accordingly.

  *<integer-expression3\>*
 :   The day number. The day is allowed to be any integer, the date is adjusted accordingly.

 

<a name="loio0cf8ed274a1d4591baedd1691a352a48__section_uz2_rp3_wrb"/>

## Returns

DATE



<a name="loio0cf8ed274a1d4591baedd1691a352a48__section_kx5_xbv_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio0cf8ed274a1d4591baedd1691a352a48__section_bqw_1cv_vrb"/>

## Examples

-   The following statement returns the value 1998-06-12:

    ```
    SELECT YMD( 1998, 06, 12 ) FROM iq_dummy
    ```

-   If the values are outside their normal range, the date adjusts accordingly. For example, the following statement returns the value 1993-03-01:

    ```
    SELECT YMD( 1992, 15, 1 ) FROM iq_dummy
    ```

-   The following statement returns the value 1993-02-28:

    ```
    SELECT YMD ( 1992, 15, 1-1 ) FROM iq_dummy
    ```

-   The following statement returns the value 1992-02-29:

    ```
    SELECT YMD ( 1992, 3, 1-1 ) FROM iq_dummy
    ```


**Related Information**  


[YMD Function [Date and Time] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a592fc9184f21015bfa68c6078363fae.html "Returns a date value corresponding to the given year, month, and day of the month.") :arrow_upper_right:

