<!-- loioa615202184f210158ba49789b340749e -->

# CHECKPOINT Statement for Data Lake Relational Engine

Checkpoints the database.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CHECKPOINT
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa615202184f210158ba49789b340749e__IQ_Usage"/>

## Remarks

CHECKPOINT forces the database server to execute a checkpoint. Checkpoints are also performed automatically by the database server according to an internal algorithm. Applications do not normally need to issue CHECKPOINT.

Data lake Relational Engine uses checkpoints differently than OLTP databases such as SAP SQL Anywhere. OLTP databases tend to have short transactions that affect only a small number of rows. Writing entire pages to storage would be very expensive for them. Instead, OLTP databases generally write to storage at checkpoints, and write only the changed data rows.

Data lake Relational Engine is an OLAP database. A single OLAP transaction can change thousands or millions of rows of data. For this reason, the database server does not wait for a checkpoint to occur to perform physical writes. It writes updated data pages to storage after each transaction commits. For an OLAP database, writing full pages of data to storage is much more effective than writing small amounts of data at arbitrary checkpoints.

Adjusting the checkpoint time or issuing explicit checkpoints may be unnecessary. Controlling checkpoints is less important in data lake Relational Engine than in OLTP database products, because data lake Relational Engine writes the actual data pages after each transaction commits.



<a name="loioa615202184f210158ba49789b340749e__IQ_Permissions"/>

## Privileges

Requires the CHECKPOINT system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa615202184f210158ba49789b340749e__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – supported by SAP Adaptive Server Enterprise

**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

