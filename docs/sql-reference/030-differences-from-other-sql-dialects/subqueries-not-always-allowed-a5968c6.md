<!-- loioa5968c6184f210158a02d46e0a212c25 -->

# Subqueries Not Always Allowed

Unlike SAP SQL Anywhere, data lake Relational Engine does not allow subqueries to appear wherever expressions are allowed.

Data lake Relational Engine supports subqueries only as allowed in the SQL-1989 grammar, plus in the `SELECT` list of the top level query block or in the `SET` clause of an `UPDATE` statement. Data lake Relational Engine does not support SAP SQL Anywhere extensions.

Many SQL implementations allow subqueries only on the right side of a comparison operator. For example, the following command is valid in data lake Relational Engine, but is not valid in most other SQL implementations:

```
SELECT		SurName,
			BirthDate,
			(	SELECT DepartmentName 
				FROM Departments
				WHERE DepartmentID = Employees.EmployeeID
				AND DepartmentID = 200 )
FROM Employees
```

