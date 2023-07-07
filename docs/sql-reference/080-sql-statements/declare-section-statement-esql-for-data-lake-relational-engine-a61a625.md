<!-- loioa61a625184f210158217db2a1d29573b -->

# DECLARE SECTION Statement \[ESQL\] for Data Lake Relational Engine

Declares host variables in an Embedded SQL program. Host variables are used to exchange data with the database.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
EXEC SQL BEGIN DECLARE SECTION;
... <C declarations>
EXEC SQL END DECLARE SECTION;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61a625184f210158217db2a1d29573b__IQ_Usage"/>

## Remarks

A declaration section is a section of C variable declarations surrounded by the `BEGIN DECLARE SECTION` and `END DECLARE SECTION` statements. A declaration section makes the SQL preprocessor aware of C variables that are used as host variables. Not all C declarations are valid inside a declaration section.



<a name="loioa61a625184f210158217db2a1d29573b__IQ_Permissions"/>

## Privileges

None



<a name="loioa61a625184f210158217db2a1d29573b__IQ_Standards"/>

## Standards

SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa61a625184f210158217db2a1d29573b__IQ_Examples"/>

## Examples

```
EXEC SQL BEGIN DECLARE SECTION;
char *emp_lname, initials[5];
int dept;
EXEC SQL END DECLARE SECTION;
```

**Related Information**  


[BEGIN … END Statement for Data Lake Relational Engine](begin-end-statement-for-data-lake-relational-engine-a6142de.md "Groups SQL statements together.")

