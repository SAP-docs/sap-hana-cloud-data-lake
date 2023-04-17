<!-- loio816f992f6ce2101481feec3e31a965ef -->

# DROP VARIABLE Statement for Data Lake Relational Engine

Drops a connection-scope SQL variable.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP VARIABLE [ IF EXISTS ] <identifier>
```



## Parameters

 IF EXISTS clause
 :   Specify this clause to allow the statement to complete without returning an error if a variable with the specified name \(and/or owner, if specified\) is not found.

  *<identifier\>* 
 :   A valid identifier for the variable.

 

## Remarks

Connection-scope variables are also automatically dropped when the database connection is terminated.

Variables are often used for large objects, so dropping them after use or setting them to NULL can free up significant resources such as storage space and memory.



<a name="loio816f992f6ce2101481feec3e31a965ef__section_ptj_nby_m2b"/>

## Privileges

No privileges are required to drop a connection-scope variable.



## Side Effects

No side effects are associated with dropping a connection-scope variable.



## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 **Related Information**  


[CREATE VARIABLE Statement for Data Lake Relational Engine](create-variable-statement-for-data-lake-relational-engine-a619d63.md "Creates data type or a connection- or database-scope variable.")

[SET Statement \[ESQL\] for Data Lake Relational Engine](set-statement-esql-for-data-lake-relational-engine-a62516a.md "Assigns a value to a SQL variable.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")
