<!-- loio3bd546476c5f1014b357ee35550658b2 -->

# Embedded SQL Indicator Variables

Indicator variables are C variables that hold supplementary information when you are fetching or putting data.

There are several distinct uses for indicator variables:

NULL values
:   To enable applications to handle NULL values.

String truncation
:   To enable applications to handle cases when fetched values must be truncated to fit into host variables.

Conversion errors
:   To hold error information.

An indicator variable is a host variable of type a\_sql\_len that is placed immediately following a regular host variable in a SQL statement. For example, in the following INSERT statement, :ind\_phone is an indicator variable:

```
EXEC SQL INSERT INTO Employees
 VALUES (:employee_number, :employee_name,
 :employee_initials, :employee_phone:ind_phone );
```

On a fetch or execute where no rows are received from the database server \(such as when an error or end of result set occurs\), then indicator values are unchanged.

> ### Note:  
> To allow for the future use of 32 and 64-bit lengths and indicators, the use of short int for Embedded SQL indicator variables is deprecated. Use a\_sql\_len instead.

