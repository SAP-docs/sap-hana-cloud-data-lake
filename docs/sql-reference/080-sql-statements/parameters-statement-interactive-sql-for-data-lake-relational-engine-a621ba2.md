<!-- loioa621ba2684f21015b69dc6ae412d919a -->

# PARAMETERS Statement \[Interactive SQL\] for Data Lake Relational Engine

Specifies parameters to an Interactive SQL \(`dbisql`\) command file.



<a name="loioa621ba2684f21015b69dc6ae412d919a__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
PARAMETERS <parameter1>, <parameter2>, …;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa621ba2684f21015b69dc6ae412d919a__IQ_Usage"/>

## Remarks

`PARAMETERS` specifies how many parameters there are to a command file and also names those parameters so that they can be referenced later in the command file.

Parameters are referenced by putting the named parameter into the command file where you want the parameter to be substituted:

```
{parameter1};
```

There can be no spaces between the braces and the parameter name.

If a command file is invoked with fewer than the required number of parameters, `dbisql` prompts for values of the missing parameters.



<a name="loioa621ba2684f21015b69dc6ae412d919a__IQ_Permissions"/>

## Privileges

None



<a name="loioa621ba2684f21015b69dc6ae412d919a__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not applicable



<a name="loioa621ba2684f21015b69dc6ae412d919a__IQ_Examples"/>

## Examples

This `dbisql` command file takes two parameters:

```
PARAMETERS department_id, file ;
SELECT Surname
FROM Employees
WHERE DepartmentID = {department_id}
>#{file}.dat;
```

**Related Information**  


[READ Statement \[Interactive SQL\] for Data Lake Relational Engine](read-statement-interactive-sql-for-data-lake-relational-engine-a622ae5.md "Reads Interactive SQL (dbisql) statements from a file.")

