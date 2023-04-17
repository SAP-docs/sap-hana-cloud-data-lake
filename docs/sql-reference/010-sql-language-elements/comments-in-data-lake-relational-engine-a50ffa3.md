<!-- loioa50ffa3b84f210158b79859bf5c3eb1f -->

# Comments in Data Lake Relational Engine

Use comments to attach explanatory text to SQL statements or statement blocks. The database server does not execute comments.



These comment indicators are available in data lake Relational Engine:


<table>
<tr>
<th valign="top" rowspan="1">

Comment Indicator



</th>
<th valign="top" rowspan="1">

Description



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

\-- \(Double hyphen\)



</td>
<td valign="top" rowspan="1">

The database server ignores any remaining characters on the line. This is the SQL92 comment indicator.



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

// \(Double slash\)



</td>
<td valign="top" rowspan="1">

The double slash has the same meaning as the double hyphen.



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

/\* … \*/ \(Slash-asterisk\)



</td>
<td valign="top" rowspan="1">

Any characters between the two comment markers are ignored. The two comment markers might be on the same or different lines. Comments indicated in this style can be nested. This style of commenting is also called C-style comments.



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

% \(Percent sign\)



</td>
<td valign="top" rowspan="1">

The percent sign has the same meaning as the double hyphen. You should not use % as a comment indicator.



</td>
</tr>
</table>



> ### Note:  
> The double-hyphen and the slash-asterisk comment styles are compatible with SAP Adaptive Server Enterprise.



<a name="loioa50ffa3b84f210158b79859bf5c3eb1f__iq_refbb_145"/>

## Examples

This example illustrates the use of double-dash comments:

```
CREATE FUNCTION fullname (firstname CHAR(30), 
			lastname CHAR(30))
RETURNS CHAR(61)
-- fullname concatenates the firstname and lastname
-- arguments with a single space between.
BEGIN
	DECLARE name CHAR(61);
	SET name = firstname || ' ' || lastname;
	RETURN ( name );
END
```

This example illustrates the use of C-style comments:

```
/*
	Lists the names and employee IDs of employees
	who work in the sales department.
*/
CREATE VIEW SalesEmployee AS
SELECT emp_id, emp_lname, emp_fname
FROM "GROUPO".Employees
WHERE DepartmentID = 200
```

