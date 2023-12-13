<!-- loio473f30fba028466f85cbeb5397f95320 -->

# NUMBER Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Generates numbers starting at 1 for each successive row in the results of the query.



```
NUMBER ( * );
```



<a name="loio473f30fba028466f85cbeb5397f95320__section_yt5_smn_vrb"/>

## Result Set

INT



<a name="loio473f30fba028466f85cbeb5397f95320__section_hsr_tmn_vrb"/>

## Remarks

Use the `NUMBER` function only in a select list or a `SET` clause of an `UPDATE` statement. For example, the following statement updates each row of the `seq_id` column with a number 1 greater than the previous row. The number is applied in the order specified by the `ORDER BY` clause:

```
update empl
set seq_id = number(*)
order by empl_id;
```

In an `UPDATE` statement, if the `NUMBER (*)` function is used in the `SET` clause and the `FROM` clause specifies a one-to-many join, `NUMBER (*)` generates unique numbers that increase, but may not increment sequentially due to row elimination.

`NUMBER` can also be used to generate primary keys when using the `INSERT` from `SELECT` statement, although using `IDENTITY/AUTOINCREMENT` is a preferred mechanism for generating sequential primary keys.

> ### Note:  
> A syntax error is generated if you use `NUMBER` in a `DELETE` statement, `WHERE`clause, `HAVING` clause, `ORDER BY` clause, subquery, query involving aggregation, any constraint, `GROUP BY`, `DISTINCT`, a query containing `UNION ALL`, or a derived table.



<a name="loio473f30fba028466f85cbeb5397f95320__section_i4q_5mn_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio473f30fba028466f85cbeb5397f95320__section_h2m_vmn_vrb"/>

## Example

This statement returns the following numbered list:

```
SELECT NUMBER( * )
FROM Departments
WHERE DepartmentID > 10;
```


<table>
<tr>
<th valign="top" rowspan="1">

          number\(\*\)

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

                           4

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

                           5

</td>
</tr>
</table>

**Related Information**  


[NUMBER Function \[Miscellaneous\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a56a888784f21015bbaed2c2a214738e.html "Generates numbers starting at 1 for each successive row in the results of the query.") :arrow_upper_right:

