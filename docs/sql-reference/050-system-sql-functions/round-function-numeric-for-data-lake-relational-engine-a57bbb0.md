<!-- loioa57bbb0684f21015822ddb659e37c042 -->

# ROUND Function \[Numeric\] for Data Lake Relational Engine

Rounds the *<numeric-expression\>* to the specified *<integer-expression\>* number of places after the decimal point.



```
ROUND ( <numeric-expression>, <integer-expression> )
```



<a name="loioa57bbb0684f21015822ddb659e37c042__ROUND_parm1"/>

## Parameters

  *<numeric-expression\>* 
 :   The number, passed to the function, to be rounded.

  *<integer-expression\>*
 :   A positive integer specifies the number of significant digits to the right of the decimal point at which to round. A negative expression specifies the number of significant digits to the left of the decimal point at which to round.

 

<a name="loioa57bbb0684f21015822ddb659e37c042__ROUND_returns1"/>

## Returns

NUMERIC

When `ROUND_TO_EVEN` database option is set ON, the `ROUND` function rounds data from a data lake Relational Engine table half to the nearest even number to the integer-expression, matching the behavior of SAP SQL Anywhere table data. When the option is set to OFF, the `ROUND` function rounds data lake Relational Engine data half away from zero.



<a name="loioa57bbb0684f21015822ddb659e37c042__ROUND_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioa57bbb0684f21015822ddb659e37c042__ROUND_example1"/>

## Example

-   The following statement returns the value 123.200:

    ```
    SELECT ROUND( 123.234, 1 ) FROM iq_dummy
    ```

    Additional results of the `ROUND` function are shown in the following table:


    <table>
    <tr>
    <th valign="top" rowspan="1">

    Value


    
    </th>
    <th valign="top" rowspan="1">

    ROUND \(Value\)


    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="1">

    123.4567


    
    </td>
    <td valign="top" rowspan="1">

    round \(a.n,4\)


    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">

    123.4570


    
    </td>
    <td valign="top" rowspan="1">

    round \(a.n,3\)


    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">

    123.4600


    
    </td>
    <td valign="top" rowspan="1">

    round \(a.n,2\)


    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">

    123.5000


    
    </td>
    <td valign="top" rowspan="1">

    round \(a.n,1\)


    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">

    123.0000


    
    </td>
    <td valign="top" rowspan="1">

    round \(a.n, 0\)


    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">

    120.0000


    
    </td>
    <td valign="top" rowspan="1">

    round \(a.n,-1\)


    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">

    100.0000


    
    </td>
    <td valign="top" rowspan="1">

    round \(a.n,-2\)


    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">

    0.0000


    
    </td>
    <td valign="top" rowspan="1">

    round \(a.n,-3\)


    
    </td>
    </tr>
    </table>
    
-   In the following examples, the ROUND\_TO\_EVEN settings affects the value returned.


    <table>
    <tr>
    <th valign="top">

    ROUND \(Value\)


    
    </th>
    <th valign="top">

    ROUND\_TO\_EVEN ON


    
    </th>
    <th valign="top">

    ROUND\_TO\_EVEN OFF


    
    </th>
    <th valign="top">

    Note


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    ROUND \(convert \(double, 123.45001\), 1\)


    
    </td>
    <td valign="top">

    123.5


    
    </td>
    <td valign="top">

    123.5


    
    </td>
    <td valign="top">

    0.05001 is more than half of 0.1


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    ROUND \(convert \(double, 123.45000\), 1\)


    
    </td>
    <td valign="top">

    123.4


    
    </td>
    <td valign="top">

    123.5


    
    </td>
    <td valign="top">

    0.0500 is half of 0.1


    
    </td>
    </tr>
    </table>
    

**Related Information**  


[TRUNCNUM Function \[Numeric\] for Data Lake Relational Engine](truncnum-function-numeric-for-data-lake-relational-engine-a58baf5.md "Truncates a number at a specified number of places after the decimal point.")

[ROUND Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/9f767014ddd542479d75822573eec6cd.html "Rounds the numeric-expression to the specified integer-expression number of places after the decimal point.") :arrow_upper_right:

