<!-- loioaea8c4095b5a436ba6ad76a6d5342a5f -->

# Subqueries in Expressions in Data Lake Relational Engine \(SAP HANA DB-Managed\)

A subquery is a SELECT statement enclosed in parentheses. The SELECT statement can contain one and only one select list item. When used as an expression, a scalar subquery is allowed to return only zero or one value.



Within the SELECT list of the top level SELECT, or in the SET clause of an UPDATE statement, you can use a scalar subquery anywhere that you can use a column name. However, the subquery cannot appear inside a conditional expression:

-   CASE
-   IF
-   NULLIF
-   ARGN
-   COALESCE
-   ISNULL

For example, the following statement returns the number of employees in each department, grouped by department name:

```
SELECT DepartmentName, COUNT(*), ‘out of’,
(SELECT COUNT(*) FROM Employees)
FROM Departments AS D, Employees AS E
WHERE D.DepartmentID = E.DepartmentID
GROUP BY DepartmentName;
```

