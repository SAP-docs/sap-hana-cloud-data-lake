<!-- loio3be5fc9b6c5f1014b006cf0d1a0c90ef -->

# sa\_rowgenerator System Procedure for Data Lake Relational Engine

Returns a result set with rows between a specified start and end value.



<a name="loio3be5fc9b6c5f1014b006cf0d1a0c90ef__section_p4t_vqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_rowgenerator( [ <rstart>[, <rend>
   [, <rstep> ] ] ] )
```



<a name="loio3be5fc9b6c5f1014b006cf0d1a0c90ef__sa_rowgenerator_parm1"/>

## Parameters


<dl>
<dt><b>

*<rstart\>* 

</b></dt>
<dd>

Use this optional INTEGER parameter to specify the starting value. The default value is 0.



</dd><dt><b>

*<rend\>* 

</b></dt>
<dd>

Use this optional INTEGER parameter to specify the ending value that is greater than or equal to *<rstart\>*. The default value is 100.



</dd><dt><b>

*<rstep\>* 

</b></dt>
<dd>

Use this optional INTEGER parameter to specify the increment by which the sequence values are increased. The default value is 1.



</dd>
</dl>



<a name="loio3be5fc9b6c5f1014b006cf0d1a0c90ef__sa_rowgenerator_resultset1"/>

## Results Set


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

row\_num

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Sequence number.

</td>
</tr>
</table>



<a name="loio3be5fc9b6c5f1014b006cf0d1a0c90ef__sa_rowgenerator_remarks1"/>

## Remarks

The sa\_rowgenerator procedure can be used in the FROM clause of a query to generate a sequence of numbers. This procedure is an alternative to using the RowGenerator system table. You can use sa\_rowgenerator for such tasks as:

-   generating test data for a known number of rows in a result set.

-   generating a result set with rows for values in every range. For example, you can generate a row for every day of the month, or you can generate ranges of ZIP codes.

-   generating a query that has a specified number of rows in the result set. This may be useful for testing the performance of queries.


No rows are returned if you do not specify correct start and end values and a positive non-zero step value.

You can emulate the behavior of the RowGenerator table with the following statement:

```
SELECT row_num FROM sa_rowgenerator( 1, 255 )
```



<a name="loio3be5fc9b6c5f1014b006cf0d1a0c90ef__sa_rowgenerator_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on the procedure.



<a name="loio3be5fc9b6c5f1014b006cf0d1a0c90ef__sa_rowgenerator_sideeffects1"/>

## Side Effects

None



<a name="loio3be5fc9b6c5f1014b006cf0d1a0c90ef__sa_rowgenerator_examples1"/>

## Examples

This example uses the sa\_rowgenerator system procedure to return 5 rows.

```
CALL sa_rowgenerator( 1, 5, 1 );
```


<table>
<tr>
<th valign="top">

row\_num

</th>
</tr>
<tr>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

3

</td>
</tr>
<tr>
<td valign="top">

4

</td>
</tr>
<tr>
<td valign="top">

5

</td>
</tr>
</table>

The example returns a result set containing one row for each of the first five days of the current month.

```
SELECT DATEADD( day, row_num-1,
        YMD( DATEPART( year, CURRENT DATE ),
            DATEPART( month, CURRENT DATE ), 1 ) ) 
    AS day_of_month
    FROM sa_rowgenerator( 1, 5, 1 )
    WHERE DATEPART( month, day_of_month ) = DATEPART( month, CURRENT DATE )
    ORDER BY row_num;
```


<table>
<tr>
<th valign="top">

day\_of\_month

</th>
</tr>
<tr>
<td valign="top">

2023-10-01 00:00:00.000

</td>
</tr>
<tr>
<td valign="top">

2023-10-02 00:00:00.000

</td>
</tr>
<tr>
<td valign="top">

2023-10-03 00:00:00.000

</td>
</tr>
<tr>
<td valign="top">

2023-10-04 00:00:00.000

</td>
</tr>
<tr>
<td valign="top">

2023-10-05 00:00:00.000

</td>
</tr>
</table>

This example generates 10 rows of data and inserts them into the NewEmployees table:

```
INSERT INTO NewEmployees ( ID, Salary, Name )
    SELECT row_num, CAST( RAND() * 1000 AS INTEGER ), 'Mary'
    FROM sa_rowgenerator( 1, 10 );
```

This example uses the sa\_rowgenerator system procedure to create a view containing all integers. The value 2147483647 in this example represents the maximum signed integer that is supported.

```
CREATE VIEW Integers AS
    SELECT row_num AS n
    FROM sa_rowgenerator( 0, 2147483647, 1 );
```

This example uses the sa\_rowgenerator system procedure to create a view containing dates from 0001-01-01 to 9999-12-31. The value 3652058 in this example represents the number of days between 0001-01-01 and 9999-12-31, the earliest and latest dates that are supported.

```
CREATE VIEW Dates AS
    SELECT DATEADD( day, row_num, '0001-01-01' ) AS d
    FROM sa_rowgenerator( 0, 3652058, 1 );
```

This query returns all years between 1900 and 2058 that have 54 weeks.

```
SELECT DATEADD ( day, row_num, '1900-01-01' ) AS d, DATEPART ( week, d ) w
    FROM sa_rowgenerator ( 0, 63919, 1 )
    WHERE w = 54;
```

**Related Information**  


[sa_rowgenerator System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/7b99d032cfbe4f80bde904bee1902662.html "Returns a result set with rows between a specified start and end value.") :arrow_upper_right:

