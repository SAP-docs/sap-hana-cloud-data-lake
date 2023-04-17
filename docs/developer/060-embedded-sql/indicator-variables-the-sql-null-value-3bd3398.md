<!-- loio3bd3398a6c5f101499add8636911280d -->

# Indicator Variables: The SQL NULL Value

Do not confuse the SQL concept of NULL with the C language constant of the same name.

In the SQL language, NULL represents either an unknown attribute or inapplicable information. The C language NULL is referred to as the null pointer constant and represents a pointer value that does not point to a memory location.

When NULL is used in this documentation, it refers to the SQL database meaning given above.

NULL is not the same as any value of the column's defined type. So, something extra is required beyond regular host variables to pass NULL values to the database or receive NULL results back. **Indicator variables** are used for this purpose.



## Using Indicator Variables when Inserting NULL

An INSERT statement could include an indicator variable as follows:

```
EXEC SQL BEGIN DECLARE SECTION;
short int employee_number;
char employee_name[50];
char employee_initials[6];
char employee_phone[15];
a_sql_len ind_phone;
EXEC SQL END DECLARE SECTION; 
/*
This program fills in the employee number, 
name, initials, and phone number.
*/
if( /* Phone number is unknown */ ) {
 ind_phone = -1;
} else {
 ind_phone = 0;
}
EXEC SQL INSERT INTO Employees
 VALUES (:employee_number, :employee_name,
 :employee_initials, :employee_phone:ind_phone );
```

If the indicator variable has a value of -1, a NULL is written. If it has a value of 0, the actual value of employee\_phone is written.



## Using Indicator Variables when Fetching NULL

Indicator variables are also used when receiving data from the database. They are used to indicate that a NULL value was fetched \(indicator is negative\). If a NULL value is fetched from the database and an indicator variable is not supplied, an error is generated \(SQLE\_NO\_INDICATOR\).

