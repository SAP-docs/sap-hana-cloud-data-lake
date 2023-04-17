<!-- loioa62546b384f2101588d3bfd494dfc800 -->

# SET Statement \[T-SQL\] for Data Lake Relational Engine

Sets database options in an SAP Adaptive Server Enterprise-compatible manner.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
SET <option-name> <option-value>
```

```
<option-value> ::=
   { ANSINULL [ { ON | OFF } ]
   | ANSI_PERMISSIONS [ { ON | OFF } ]
   | CLOSE_ON_ENDTRANS ON 
   | QUOTED_IDENTIFIER [ { ON | OFF } ]
   | ROWCOUNT <integer>
   | STRING_RTRUNCATION [ { ON | OFF } ]
   | TRANSACTION ISOLATION LEVEL [ { 0 | 1 | 2 | 3 } ] }
```



<a name="loioa62546b384f2101588d3bfd494dfc800__IQ_Parameters"/>

## Parameters

 ANSINULL
 :   The default behavior for comparing values to NULL in data lake Relational Engine and SAP ASE is different. Setting ANSINULL to OFF provides Transact-SQL compatible comparisons with NULL.

  ANSI\_PERMISSIONS
 :   The default behavior in data lake Relational Engine and SAP ASE regarding permissions required to carry out a DELETE containing a column reference is different. Setting ANSI\_PERMISSIONS to OFF provides Transact-SQL-compatible permissions on DELETE.

  CLOSE\_ON\_ENDTRANS
 :   When set to ON \(the default and only allowable value\), cursors are closed at the end of a transaction. With the option set ON, CLOSE\_ON\_ENDTRANS provides Transact-SQL-compatible behavior.

  QUOTED\_IDENTIFIER
 :   Controls whether strings enclosed in double quotes are interpreted as identifiers \(ON\) or as literal strings \(OFF\).

  ROWCOUNT
 :   In the Transact-SQL, limits to the specified integer the number of rows fetched for any cursor. This includes rows fetched by repositioning the cursor. Any fetches beyond this maximum return a warning. The setting is considered when returning the estimate of the number of rows for a cursor on an `OPEN` request.

    > ### Note:  
    > Data lake Relational Engine supports the *<@@rowcount\>* global variable. `SELECT`, `INSERT`, `DELETE`, and `UPDATE` statements affect the value of the ROWCOUNT clause. The `ROWCOUNT` clause has no effect on cursor operation, the `IF` statement, or creating or dropping a table or procedure.

    In data lake Relational Engine, if ROWCOUNT is greater than the number of rows that `dbisql` can display, `dbisql` may do extra fetches to reposition the cursor. The number of rows actually displayed may be less than the number requested. Also, if any rows are refetched due to truncation warnings, the count might be inaccurate.

    A value of zero resets the option to get all rows.

  STRING\_RTRUNCATION
 :   The default behavior in data lake Relational Engine and SAP ASE when nonspace characters are truncated on assigning SQL string data is different. Setting STRING\_RTRUNCATION to ON provides Transact-SQL-compatible string comparisons, including hexadecimal string \(binary data type\) comparisons.

  TRANSACTION ISOLATION LEVEL
 :   Sets the locking isolation level for the current connection For SAP ASE, only 1 and 3 are valid options. For data lake Relational Engine, only 3 is a valid option.

  SET PREFETCH
 :   Is allowed by data lake Relational Engine for compatibility, but has no effect.

 

<a name="loioa62546b384f2101588d3bfd494dfc800__IQ_Usage"/>

## Remarks

Database options in data lake Relational Engine are set using the `SET OPTION` statement. However, data lake Relational Engine also provides support for the SAP ASE `SET` statement for a set of options particularly useful for compatibility.



<a name="loioa62546b384f2101588d3bfd494dfc800__IQ_Permissions"/>

## Privileges

None



<a name="loioa62546b384f2101588d3bfd494dfc800__IQ_Standards"/>

## Standards

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar
-   SAP database products – data lake Relational Engine supports a subset of the SAP ASE database options.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

