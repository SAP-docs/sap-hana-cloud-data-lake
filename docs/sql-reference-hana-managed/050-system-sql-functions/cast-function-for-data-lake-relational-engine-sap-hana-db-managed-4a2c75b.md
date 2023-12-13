<!-- loio4a2c75bbed1d4b399e51f704ee7d35dc -->

# CAST Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the value of an expression converted to a supplied data type.



```
CAST ( <expression> AS <data type> );
```



<a name="loio4a2c75bbed1d4b399e51f704ee7d35dc__section_bg2_v5l_srb"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The expression to be converted.



</dd><dt><b>

*<data type\>*

</b></dt>
<dd>

The data type to cast the expression into. Set the data type explicitly, or specify the %TYPE attribute to set the data type to the data type of a column in a table or view, or to the data type of a variable.



</dd>
</dl>



<a name="loio4a2c75bbed1d4b399e51f704ee7d35dc__section_bgr_v5l_srb"/>

## Result Set

The specified data type.



<a name="loio4a2c75bbed1d4b399e51f704ee7d35dc__section_fmn_w5l_srb"/>

## Remarks

If you do not indicate a length for character string types, data lake Relational Engine chooses an appropriate length. If neither precision nor scale is specified for a DECIMAL conversion, the database server selects appropriate values.

Set the data type explicitly, or specify the %TYPE attribute to set the data type to the data type of a column in a table or view, or to the data type of a variable. For example:

```
SELECT CAST( NULL AS NUMERIC ) A,
       CAST( NULL AS NUMERIC(15,2) ) B;
```

is described as:

```
A NUMERIC(1,0);
B NUMERIC(15,2);
```



<a name="loio4a2c75bbed1d4b399e51f704ee7d35dc__section_jb1_x5l_srb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loio4a2c75bbed1d4b399e51f704ee7d35dc__section_uqv_qfj_wrb"/>

## Examples

-   The following function ensures a string is used as a date:

    ```
    CAST( '2000-10-31' AS DATE );
    ```

-   The following is the value of the expression `1 + 2`. The data type to cast the expression into. Set the data type is calculated, and the result cast into a single-character string, the length the data server assigns:

    ```
    CAST( 1 + 2 AS CHAR );
    ```

-   You can use the `CAST` function to shorten strings:

    ```
    SELECT CAST( lname AS CHAR(5) ) FROM Customers;
    ```


**Related Information**  


[CAST Function \[Data Type Conversion\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a53996d784f21015a34086a244c40db1.html "Returns the value of an expression converted to a supplied data type.") :arrow_upper_right:

