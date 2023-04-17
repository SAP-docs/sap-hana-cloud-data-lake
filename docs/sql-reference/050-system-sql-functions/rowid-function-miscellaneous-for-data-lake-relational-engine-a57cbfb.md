<!-- loioa57cbfb484f21015b1a6f34fe17463d2 -->

# ROWID Function \[Miscellaneous\] for Data Lake Relational Engine

Returns the internal row ID value for each row of the table.



```
ROWID ( <table-name> ) … FROM <table-name>
```



<a name="loioa57cbfb484f21015b1a6f34fe17463d2__ROWID_parm1"/>

## Parameters

 *<table-name\>*
 :   The name of the table. Specify the name of the table within the parentheses with either no quotes or with double quotes.

 

<a name="loioa57cbfb484f21015b1a6f34fe17463d2__ROWID_returns1"/>

## Returns

UNSIGNED BIGINT



<a name="loioa57cbfb484f21015b1a6f34fe17463d2__ROWID_remarks1"/>

## Remarks

You can use the `ROWID` function with other clauses to manipulate specific rows of the table.

You must specify the `FROM` *<table-name\>* clause.



<a name="loioa57cbfb484f21015b1a6f34fe17463d2__ROWID_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa57cbfb484f21015b1a6f34fe17463d2__ROWID_examples1"/>

## Examples

-   The following statement returns the row ID values 1 through 10:

    ```
    SELECT ROWID( "PRODUCTS" ) FROM PRODUCTS
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
    WHERE PRODUCTS.ID < 400
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
    WHERE ROWID ( PRODUCTS ) > 50
    ```


**Related Information**  


[ROWID Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/77bc1bdbb46f48368bb3398b4cabaea0.html "Returns the internal row ID value for each row of the table.") :arrow_upper_right:

