<!-- loio3be4974b6c5f1014b57acc65b617ca45 -->

# DROP TRIGGER Statement for Data Lake Relational Engine

Removes a trigger from the database.This statement applies to data lake Relational Engine catalog store tables only. 



<a name="loio3be4974b6c5f1014b57acc65b617ca45__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP TRIGGER [ IF EXISTS ] [ <owner>.][<table-name>.]<trigger-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



## Remarks

Use the IF EXISTS clause if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.



<a name="loio3be4974b6c5f1014b57acc65b617ca45__section_v2w_1dz_m2b"/>

## Privileges

To drop a trigger on a table, one of the following conditions must be true:

-   You are the owner of the table.

-   You have ALTER privilege on the table.

-   You have the ALTER ANY TABLE system privilege.

-   You have the ALTER ANY OBJECT system privilege.


To drop a trigger on a view owned by someone else, requires one of:

-   ALTER ANY VIEW system privilege
-   ALTERANY OBJECT system privilege

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



## Side Effects

Automatic commit.



## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

DROP TRIGGER comprises part of optional ANSI/ISO SQL Language Feature T211, "Basic trigger capability". The IF EXISTS clause is not in the standard.



</dd>
</dl>



## Example

This example creates, and then drops, a trigger called emp\_upper\_postal\_code that ensures postal codes are in upper case before updating the Employees table. If the trigger does not exist, an error is returned.

```
CREATE TRIGGER emp_upper_postal_code
BEFORE UPDATE OF PostalCode
ON GROUPO.Employees
REFERENCING NEW AS new_emp
FOR EACH ROW
WHEN ( ISNUMERIC( new_emp.PostalCode ) = 0 )
BEGIN
   -- Ensure postal code is uppercase (employee might be 
   -- in Canada where postal codes contain letters)
   SET new_emp.PostalCode = UPPER(new_emp.PostalCode)
END;
DROP TRIGGER emp_upper_postal_code;
```

**Related Information**  


[ALTER TRIGGER Statement for Data Lake Relational Engine](alter-trigger-statement-for-data-lake-relational-engine-3be445c.md "Replaces a trigger definition with a modified version. You must include the entire new trigger definition in the ALTER TRIGGER statement. This statement applies to data lake Relational Engine catalog store tables only.")

[CREATE TRIGGER Statement for Data Lake Relational Engine](create-trigger-statement-for-data-lake-relational-engine-3be4860.md "Creates a trigger on a table. This statement applies to data lake Relational Engine catalog store tables only.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

