<!-- loiod42de2d8355a4762b5a47e810d55653f -->

# DROP FUNCTION Statement for Data Lake Relational Engine

Removes a user-defined function from the database.



<a name="loiod42de2d8355a4762b5a47e810d55653f__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP FUNCTION [ IF EXISTS ] [ { <owner> | <schema-name> }.]<function-name> 
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiod42de2d8355a4762b5a47e810d55653f__drop_function_param1"/>

## Parameters


<dl>
<dt><b>

IF EXISTS

</b></dt>
<dd>

Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.



</dd>
</dl>



<a name="loiod42de2d8355a4762b5a47e810d55653f__drop_function_remarks1"/>

## Remarks

None



<a name="loiod42de2d8355a4762b5a47e810d55653f__drop_function_priv1"/>

## Privileges



### 

-   Requires one of:
    -   You own the procedure.
    -   DROP ANY PROCEDURE system privilege
    -   DROP ANY OBJECT system privilege
    -   DROP object-level privilege on the procedure
    -   DROP object-level privilege on the schema containing the procedure if the schema is owned by another user.


See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loiod42de2d8355a4762b5a47e810d55653f__drop_function_side_effects1"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loiod42de2d8355a4762b5a47e810d55653f__drop_function_standards1"/>

## Standards

-   SQL – ISO/ANSI SQL compliant



<a name="loiod42de2d8355a4762b5a47e810d55653f__drop_function_examples"/>

## Examples

This example drops the user-defined function myfunction1 if it exists from the database.

```
DROP FUNCTION IF EXISTS myfunction1;
```

**Related Information**  


[CREATE FUNCTION Statement for Data Lake Relational Engine](create-function-statement-for-data-lake-relational-engine-a61796c.md "Creates a user-defined function in the database. A function can be created for another user by specifying an owner name. Subject to permissions, a user-defined function can be used in exactly the same way as other non-aggregate functions.")

[ALTER FUNCTION Statement for Data Lake Relational Engine](alter-function-statement-for-data-lake-relational-engine-a61280a.md "Modifies an existing function. Include the entire modified function in the ALTER FUNCTION statement.")

[DROP FUNCTION Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/58c58a93e1de4d409e3776c4b92790e1.html "Removes a user-defined function from the database.") :arrow_upper_right:

