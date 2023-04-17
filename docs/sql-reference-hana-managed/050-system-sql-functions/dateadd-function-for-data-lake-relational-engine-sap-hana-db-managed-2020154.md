<!-- loio202015428c2c49239a2aec8d572a0613 -->

# DATEADD Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the date produced by adding the specified number of the specified date parts to a date.



```
DATEADD ( <date-part>, <numeric-expression>, <date-expression> )
```



<a name="loio202015428c2c49239a2aec8d572a0613__section_fyw_1gm_srb"/>

## Parameters

 *<date-part\>*
 :   The date part to be added to the date.

  *<numeric-expression\>*
 :   The number of date parts to be added to the date. *<numeric-expression\>* can be any numeric type; the value is truncated to an integer. The maximum microsecond in *<numeric-expression\>* is 2147483647, that is, 35:47.483647 \(35 minutes 47 seconds 483647 microseconds\).

  *<date-expression\>*
 :   The date expression in the format `{ date | time | timestamp }`.

 

<a name="loio202015428c2c49239a2aec8d572a0613__section_qkn_bgm_srb"/>

## Returns

The result type is based on the *<date\_expression\>* type.



<a name="loio202015428c2c49239a2aec8d572a0613__section_v51_cgm_srb"/>

## Remarks

DATEADD is a Transact-SQL compatible data manipulation function.



<a name="loio202015428c2c49239a2aec8d572a0613__section_bzl_cgm_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio202015428c2c49239a2aec8d572a0613__section_vqw_cgm_srb"/>

## Examples

-   The following statement returns the value 1995-11-02 00:00:00.000:

    ```
    SELECT DATEADD( MONTH, 102, '1987/05/02' ) FROM iq_dummy
    ```

-   The following statement returns the value 2009-11-10 14:57:52.722016:

    ```
    SELECT DATEADD(MICROSECOND, 15, '2009-11-10
    14:57:52.722001') FROM iq_dummy
    ```

-   The following statement returns the value 1985-05-02 00:00:00.123456:

    ```
    SELECT DATEADD(MICROSECOND, 123456, '1985/05/02')
    FROM iq_dummy
    ```

-   The following statement returns the value 1985-05-01 23:59:59.876544:

    ```
    SELECT DATEADD(MICROSECOND, -123456, '1985/05/02')
    FROM iq_dummy
    ```

-   The following statement returns the value 2009-11-03 11:10:42.033192:

    ```
    SELECT DATEADD(MCS, 2, '2009-11-03 11:10:42.033190')
    FROM iq_dummy
    ```


**Related Information**  


[DATEADD Function [Date and Time] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a5449deb84f210159a75e748a099539f.html "Returns the date produced by adding the specified number of the specified date parts to a date.") :arrow_upper_right:

