<!-- loioa6161aef84f210158aedf72e43917471 -->

# CONFIGURE Statement \[Interactive SQL\] for Data Lake Relational Engine

Activates the Interactive SQL \(`dbisql`\) configuration window.



<a name="loioa6161aef84f210158aedf72e43917471__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CONFIGURE;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa6161aef84f210158aedf72e43917471__IQ_Usage"/>

## Remarks

The `dbisql` configuration window displays the current settings of all `dbisql` options. It does not display or let you modify database options.

If you select Permanent, the options are written to the `SYSOPTION` table in the database and the database server performs an automatic `COMMIT`. If you do not choose Permanent, and instead click OK, options are set temporarily and remain in effect only for the current database connection.



<a name="loioa6161aef84f210158aedf72e43917471__IQ_Permissions"/>

## Privileges

None



<a name="loioa6161aef84f210158aedf72e43917471__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

