<!-- loiobd71ba2eab21415e8d3ce875005fc9b9 -->

# COUNT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Counts the number of rows in a group, depending on the specified parameters.



```
COUNT ( * | <expression> | DISTINCT <column-name> )
```



<a name="loiobd71ba2eab21415e8d3ce875005fc9b9__section_l1v_gnl_srb"/>

## Parameters

 \*
 :   Returns the number of rows in each group.

    > ### Note:  
    > When the query results are displayed, the \* is not displayed in the column header, and appears as:
    > 
    > ```
    > Count()
    > ```

  *<expression\>*
 :   Returns the number of rows in each group where expression is not the NULL value.

  DISTINCT *<column-name\>*
 :   Returns the number of different values in column-name. Rows where the value is the NULL value are not included in the count.

 

<a name="loiobd71ba2eab21415e8d3ce875005fc9b9__section_pkj_hnl_srb"/>

## Returns

UNSIGNED BIGINT



<a name="loiobd71ba2eab21415e8d3ce875005fc9b9__section_ylr_knl_srb"/>

## Remarks

Specifying COUNT \(\) is equivalent to specifying COUNT \( \* \).



<a name="loiobd71ba2eab21415e8d3ce875005fc9b9__section_w2d_lnl_srb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loiobd71ba2eab21415e8d3ce875005fc9b9__section_b3c_mnl_srb"/>

## Example

Returns each unique city, and the number of rows with that city value:

```
SELECT city , Count(*)
FROM Employees
GROUP BY city
```

**Related Information**  


[COUNT Function [Aggregate] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a54290fd84f21015b7dddc9484de19d0.html "Counts the number of rows in a group, depending on the specified parameters.") :arrow_upper_right:

