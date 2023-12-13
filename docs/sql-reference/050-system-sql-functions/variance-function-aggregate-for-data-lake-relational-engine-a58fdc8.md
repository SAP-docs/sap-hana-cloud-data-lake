<!-- loioa58fdc8684f210158b82f182e03b637a -->

# VARIANCE Function \[Aggregate\] for Data Lake Relational Engine

Returns the variance of a set of numbers.



```
VARIANCE ( [ ALL ] <expression> );
```



<a name="loioa58fdc8684f210158b82f182e03b637a__VARIANCE_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Any numeric data type \(`FLOAT`, `REAL`, or `DOUBLE`\) expression.

The expression \(commonly a column name\) whose sample-based variance is calculated over a set of rows.



</dd>
</dl>



<a name="loioa58fdc8684f210158b82f182e03b637a__VARIANCE_returns1"/>

## Result Set

DOUBLE



<a name="loioa58fdc8684f210158b82f182e03b637a__VARIANCE_remarks1"/>

## Remarks

The formula used to calculate `VARIANCE` is

![The formula used by the VARIANCE function to calculate variance is var equals n times the sum of x squared minus the sum of x squared divided by n times n minus one](images/variance_gif_a16f632.gif)

`VARIANCE` returns a result of data type `double-precision floating-point`. If applied to the empty set, the result is NULL, which returns NULL for a one-element input set.

`VARIANCE` does not support the keyword DISTINCT. A syntax error is returned if DISTINCT is used with `VARIANCE`.



<a name="loioa58fdc8684f210158b82f182e03b637a__VARIANCE_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa58fdc8684f210158b82f182e03b637a__VARIANCE_examples1"/>

## Examples

-   Given this data:

    ```
    SELECT Salary FROM Employees WHERE DepartmentID = 300;
    ```


    <table>
    <tr>
    <th valign="top" rowspan="1">

          salary
    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
     51432.000
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
     57090.000
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
     42300.000
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
       43700.00
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
      36500.000
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    138948.000
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
      31200.000
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
        58930.00
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
        75400.00
    
    </td>
    </tr>
    </table>
    
    The following statement returns the value 1063923790.99999994:

    ```
    SELECT VARIANCE ( Salary ) FROM Employees
    WHERE DepartmentID = 300;
    ```

-   Given this data:

    ```
    SELECT UnitPrice FROM Products WHERE name = 'Tee Shirt';
    ```


    <table>
    <tr>
    <th valign="top" rowspan="1">

    UnitPrice
    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
                9.00
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
              14.00
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
              14.00
    
    </td>
    </tr>
    </table>
    
    The following statement returns the value 8.33333333333334327:

    ```
    SELECT VARIANCE ( UnitPrice ) FROM Products
    WHERE name = 'Tee Shirt';
    ```


**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[VARIANCE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/974f709b109d4fb1bfe049dc4b05d7de.html "Returns the variance of a set of numbers.") :arrow_upper_right:

