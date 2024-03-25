<!-- loio77bc1bdbb46f48368bb3398b4cabaea0 -->

# ROWID Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the internal row ID value for each row of the table.



```
ROWID ( <table-name> ) … FROM <table-name>;
```



<a name="loio77bc1bdbb46f48368bb3398b4cabaea0__section_td5_4rt_vrb"/>

## Parameters


<dl>
<dt><b>

*<table-name\>*

</b></dt>
<dd>

The name of the table. Specify the name of the table within the parentheses with either no quotes or with double quotes.



</dd>
</dl>



<a name="loio77bc1bdbb46f48368bb3398b4cabaea0__section_xjj_prt_vrb"/>

## Result Set

UNSIGNED BIGINT



<a name="loio77bc1bdbb46f48368bb3398b4cabaea0__section_dk5_qrt_vrb"/>

## Remarks

You can use the `ROWID` function with other clauses to manipulate specific rows of the table.

You must specify the `FROM` *<table-name\>* clause.



<a name="loio77bc1bdbb46f48368bb3398b4cabaea0__section_f4v_f43_wrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio77bc1bdbb46f48368bb3398b4cabaea0__section_hwj_g43_wrb"/>

## Examples

-   The following statement returns the row ID values 1 through 10:

    ```
    SELECT ROWID( "PRODUCTS" ) FROM PRODUCTS;
    ```


    <table>
    <tr>
    <th valign="top" rowspan="1">

    rowid\(Products\)
    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    1
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    2
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    3
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    .
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    .
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    .
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    10
    
    </td>
    </tr>
    </table>
    
-   The following statement returns the product ID and row ID value of all rows with a product ID value less than 400:

    ```
    SELECT PRODUCTS.ID, ROWID ( PRODUCTS )
    FROM PRODUCTS
    WHERE PRODUCTS.ID < 400;
    ```


    <table>
    <tr>
    <th valign="top" rowspan="1">

    ID
    
    </th>
    <th valign="top" rowspan="1">

    rowid \(Products\)
    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    300
    
    </td>
    <td valign="top" rowspan="1">
    
    1
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    301
    
    </td>
    <td valign="top" rowspan="1">
    
    2
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    302
    
    </td>
    <td valign="top" rowspan="1">
    
     3
    
    </td>
    </tr>
    </table>
    
-   The following statement deletes all rows with row ID values greater than 50:

    ```
    DELETE FROM PRODUCTS
    WHERE ROWID ( PRODUCTS ) > 50;
    ```


**Related Information**  


[ROWID Function \[Miscellaneous\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a57cbfb484f21015b1a6f34fe17463d2.html "Returns the internal row ID value for each row of the table.") :arrow_upper_right:

