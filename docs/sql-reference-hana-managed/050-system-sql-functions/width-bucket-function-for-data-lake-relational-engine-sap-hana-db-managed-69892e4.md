<!-- loio69892e4fa52c4ad885c269d8009f06c3 -->

# WIDTH\_BUCKET Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

For a given expression, the `WIDTH_BUCKET` function returns the bucket number that the result of this expression will be assigned after it is evaluated.



```
WIDTH_BUCKET ( <expression>, <min_value>, <max_value>, <num_buckets> )
```



<a name="loio69892e4fa52c4ad885c269d8009f06c3__section_swk_jdv_vrb"/>

## Parameters

 *<expression\>*
 :   The expression for which the histogram is being created. This expression must evaluate to a numeric or datetime value or to a value that can be implicitly converted to a numeric or datetime value. If *<expr\>* evaluates to null, then the expression returns null.

  *<min\_value\>*
 :   An expression that resolves to the end points of the acceptable range for *<expr\>*. Must also evaluate to numeric or datetime values and cannot evaluate to null.

  *<max\_value\>*
 :   An expression that resolves to the end points of the acceptable range for *<expr\>*. Must also evaluate to numeric or datetime values and cannot evaluate to null.

  *<num\_buckets\>*
 :   Is an expression that resolves to a constant indicating the number of buckets. This expression must evaluate to a positive integer.

 

<a name="loio69892e4fa52c4ad885c269d8009f06c3__section_d1c_kdv_vrb"/>

## Remarks

You can generate equi-width histograms with the `WIDTH_BUCKET` function. Equi-width histograms divide data sets into buckets whose interval size \(highest value to lowest value\) is equal. The number of rows held by each bucket will vary. A related function, `NTILE`, creates equi-height buckets.

Equi-width histograms can be generated only for numeric, date or datetime data types; therefore, the first three parameters should be all numeric expressions or all date expressions. Other types of expressions are not allowed. If the first parameter is NULL, the result is NULL. If the second or the third parameter is NULL, an error message is returned, as a NULL value cannot denote any end point \(or any point\) for a range in a date or numeric value dimension. The last parameter \(number of buckets\) should be a numeric expression that evaluates to a positive integer value; 0, NULL, or a negative value will result in an error.

Buckets are numbered from 0 to \(n+1\). Bucket 0 holds the count of values less than the minimum. Bucket\(n+1\) holds the count of values greater than or equal to the maximum specified value.



<a name="loio69892e4fa52c4ad885c269d8009f06c3__section_aws_kdv_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio69892e4fa52c4ad885c269d8009f06c3__section_bhh_ldv_vrb"/>

## Example

The following example creates a 10-bucket histogram on the `credit_limit` column for customers in Massachusetts in the sample table and returns the bucket number \(“Credit Group”\) for each customer. Customers with credit limits greater than the maximum value are assigned to the overflow bucket, 11:

```
select EmployeeID, Surname, Salary, WIDTH_BUCKET(Salary, 29000, 60000, 4)
 "Wages" from Employees where State = 'FL' order by "Wages"
```

```
EMPLOYEEID   SURNAME               SALARY         Wages
----------   -------               ------         -----
888          Charlton           28300.000             0
1390         Litton             58930.000             4
207          Francis            53870.000             4
266          Gowda              59840.000             4
445          Lull               87900.000             5
1021         Sterling           64900.000             5
902          Kelly              87500.000             5
1576         Evans              68940.000             5
```

When the bounds are reversed, the buckets are open-closed intervals. For example: `WIDTH_BUCKET` \(*<credit\_limit\>*, *<5000\>*, *<0\>*, *<5\>*\). In this example, bucket number 1 is \(4000, 5000\), bucket number 2 is \(3000, 4000\), and bucket number 5 is \(0, 1000\). The overflow bucket is numbered 0 \(5000, +infinity\), and the underflow bucket is numbered 6 \(-infinity, 0\).

**Related Information**  


[WIDTH_BUCKET Function [Numeric] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a591658384f21015a3a2e821679c9000.html "For a given expression, the WIDTH_BUCKET function returns the bucket number that the result of this expression will be assigned after it is evaluated.") :arrow_upper_right:

