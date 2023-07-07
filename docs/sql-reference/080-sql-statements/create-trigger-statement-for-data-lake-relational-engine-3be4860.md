<!-- loio3be486006c5f10148430849495d4e67e -->

# CREATE TRIGGER Statement for Data Lake Relational Engine

Creates a trigger on a table.This statement applies to data lake Relational Engine catalog store tables only. 



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE [ OR REPLACE ] TRIGGER [<owner>.][<table-name>.]<trigger-name> 
   <trigger-type>
   { <trigger-event>[, ...  ] | UPDATE OF <column-name>[, ...] }
   [ ORDER <integer> ] ON <table-name>
   [ REFERENCING [ OLD AS <old-name> ]
      [ NEW AS <new-name> ] 
      [ REMOTE AS <remote-name> ] ]
   [ FOR EACH { ROW | STATEMENT } ]
   [ WHEN ( <search-condition> ) ]
<trigger-body>
```

```
<trigger-type> : 
   { BEFORE 
   | AFTER 
   | INSTEAD OF 
   | RESOLVE }
```

```
<trigger-event> : 
   { DELETE 
   | INSERT 
   | UPDATE }
```

```
<trigger-body> : a BEGIN statement that optionally includes boolean logic keywords 
   ( { IF | ELSIF } { INSERTING | UPDATING | DELETING } THEN <some-action> )
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



## Parameters


<dl class="glossary">
<dt><b>

OR REPLACE clause

</b></dt>
<dd>

Specifying OR REPLACE creates a new trigger, or replaces an existing trigger with the same name.



</dd>
</dl>


<dl class="glossary">
<dt><b>

 *<trigger-type\>* 

</b></dt>
<dd>

Row-level triggers can be defined to execute BEFORE, AFTER, or INSTEAD OF an insert, update, or delete operation. Statement-level triggers can be defined to execute INSTEAD OF or AFTER the statement.

BEFORE UPDATE triggers fire any time an UPDATE occurs on a row, whenever the new value differs from the old value. That is, if a *<column-list\>* is specified for a BEFORE UPDATE trigger, then the trigger fires if any of the columns in *<column-list\>* appear in the SET clause of the UPDATE statement. If a *<column-list\>* is specified for an AFTER UPDATE trigger, then the trigger is fired only if the value of any of the columns in *<column-list\>* is *changed* by the UPDATE statement.

INSTEAD OF triggers are the only form of trigger that you can define on a regular view. INSTEAD OF triggers replace the triggering action with another action. When an INSTEAD OF trigger fires, the triggering action is skipped and the specified action is performed. INSTEAD OF triggers can be defined as a row-level or a statement-level trigger. A statement-level INSTEAD OF trigger replaces the entire statement, including all row-level operations. If a statement-level INSTEAD OF trigger fires, then no row-level triggers fire as a result of that statement. However, the body of the statement-level trigger could perform other operations that, in turn, cause other row-level triggers to fire.

If you are defining an INSTEAD OF trigger, then you cannot use the UPDATE OF *<column-list\>* clause, the ORDER clause, or the WHEN clause.



</dd><dt><b>

 *<trigger-event\>* 

</b></dt>
<dd>

When defining a trigger, you can combine DELETE, INSERT, and UPDATE events in the same definition, but triggers for UPDATE OF events must be defined separately. You can define any number of DELETE, INSERT, and UPDATE triggers on a table. You can define any number of triggers for UPDATE OF events on a table, but only one per column.

Triggers can be fired by the following events:


<dl>
<dt><b>

DELETE event

</b></dt>
<dd>

The trigger is invoked whenever one or more rows of the table are deleted.



</dd><dt><b>

INSERT event

</b></dt>
<dd>

The trigger is invoked whenever one or more rows are inserted into the table.



</dd><dt><b>

UPDATE event

</b></dt>
<dd>

The trigger is invoked whenever one or more rows of the table are updated.

The keyword UPDATING is also supported for this clause for compatibility with other SQL dialects. The argument for UPDATING is a quoted string \(for example, `UPDATING( 'mycolumn' )`\), whereas the argument for UPDATE is an identifier \(for example, `UPDATE( mycolumn )`\).



</dd><dt><b>

UPDATE OF *<column-list\>* event

</b></dt>
<dd>

The trigger is invoked whenever a row of the associated table is updated and a column in the *<column-list\>* is modified. This type of trigger event cannot be used in a *<trigger-event-list\>*; it must be the only trigger event defined for the trigger. This clause cannot be used in an INSTEAD OF trigger.

You can only specify one UPDATE OF trigger per column.

You can write separate triggers for each event that you need to handle or, if you have some shared actions and some actions that depend on the event, you can create a trigger for all events and use an IF statement to distinguish the action taking place.



</dd>
</dl>



</dd><dt><b>

ORDER clause

</b></dt>
<dd>

It is good practice to specify order for triggers when defining multiple triggers on a table, even if they are not the same type. This ensures predictable results and makes easier to confirm which order they are processed in.

When defining additional triggers of the same type \(insert, update, or delete\) to fire at the same time \(before, after, or resolve\), you must specify an ORDER clause to tell the database server the order in which to fire the triggers. Order numbers must be unique among same-type triggers configured to fire at the same time. If you specify an order number that is not unique, then an error is returned. Order numbers do not need to be in consecutive order \(for example, you could specify 1, 12, 30\). The database server fires the triggers starting with the lowest number.

Typically, if you omit the ORDER clause, or specify 0, then the database server assigns the order of 1. However, if another same-type trigger is already set to 1, then an error is returned.

When you create additional triggers that contain *multiple* event types, if you omit the ORDER clause, and one or more of the event types is the same as in other triggers \(for example, the *trigger-event-list* for one trigger is UPDATE, INSERT, and the *trigger-event-list* for another trigger is UPDATE\), the database server does not return an error. In this case, the database server processes the triggers in an implementation-specific order that may not be expected and is subject to change. Therefore, it is strongly recommended that you always specify an ORDER clause when defining more than one trigger on a table.

When adding additional triggers, you may need to modify the existing same-type triggers for the event, depending on whether the actions of the triggers interact. If they do not interact, then the new trigger must have an ORDER value unique from other existing triggers. If they do interact, you need to consider what the other triggers do, and you may need to change the order in which they fire.

The ORDER clause is not supported for INSTEAD OF triggers since there can only be one INSTEAD OF trigger of each type \(insert, update, or delete\) defined on a table or view.



</dd><dt><b>

REFERENCING clause

</b></dt>
<dd>

The REFERENCING OLD and REFERENCING NEW clauses allow you to refer to the inserted, deleted, or updated rows. With this clause an UPDATE is treated as a delete followed by an insert.

An INSERT takes the REFERENCING NEW clause, which represents the inserted row. There is no REFERENCING OLD clause.

A DELETE takes the REFERENCING OLD clause, which represents the deleted row. There is no REFERENCING NEW clause.

An UPDATE takes the REFERENCING OLD clause, which represents the row before the update, and it takes the REFERENCING NEW clause, which represents the row after the update.

The meanings of REFERENCING OLD and REFERENCING NEW differ, depending on whether the trigger is a row-level or a statement-level trigger. For row-level triggers, the REFERENCING OLD clause allows you to refer to the values in a row before an update or delete, and the REFERENCING NEW clause allows you to refer to the inserted or updated values. The OLD and NEW rows can be referenced in BEFORE and AFTER triggers. The REFERENCING NEW clause allows you to modify the new row in a BEFORE trigger before the insert or update operation takes place.

For statement-level triggers, the REFERENCING OLD and REFERENCING NEW clauses refer to declared temporary tables holding the old and new values of the rows.



</dd><dt><b>

FOR EACH clause

</b></dt>
<dd>

To declare a trigger as a row-level trigger, use the FOR EACH ROW clause. To declare a trigger as a statement-level trigger, you can either use a FOR EACH STATEMENT clause or omit the FOR EACH clause. For clarity, it is recommended that you specify the FOR EACH STATEMENT clause if you are declaring a statement-level trigger.



</dd><dt><b>

WHEN clause

</b></dt>
<dd>

The trigger fires only for rows where the search-condition evaluates to true. The WHEN clause can be used only with row level triggers. This clause cannot be used in an INSTEAD OF trigger.



</dd><dt><b>

 *<trigger-body\>* 

</b></dt>
<dd>

The trigger body contains the actions to take when the triggering action occurs, and consists of a BEGIN statement.

You can include trigger operation conditions in the BEGIN statement. Trigger operation conditions perform actions depending on the trigger event that caused the trigger to fire. For example, if the trigger is defined to fire for both updates and deletes, you can specify different actions for the two conditions.

You can also use Boolean conditions <code>{ INSERTING | DELETING | UPDATING [ ( '<i class="varname">&lt;col-name&gt;</i>' ) ] }</code> anywhere a condition can be used in the body of the trigger. This special syntax enables you to specify an additional action to take when performing some *<trigger-event\>*. For example, `IF INSERTING THEN SET msg = msg || 'insert'`.



</dd>
</dl>



## Remarks

The CREATE TRIGGER statement creates a trigger associated with a table in the database, and stores the trigger in the database.

You cannot define a trigger on a materialized view. If you do, a SQLE\_INVALID\_TRIGGER\_MATVIEW error is returned.

A trigger is declared as either a row-level trigger, in which case it executes before or after each row is modified, or a statement-level trigger, in which case it executes after the entire triggering statement is completed.

CREATE TRIGGER puts a table lock on the table and requires exclusive use of the table.



<a name="loio3be486006c5f10148430849495d4e67e__section_scf_3fz_m2b"/>

## Privileges

To create a trigger on a self owned view, requires one of:

-   CREATE ANY TRIGGER system privilege
-   CREATE ANY OBJECT system privilege

Additionally, you must be the owner of the table the trigger is built on or have one of the following privileges:

-   ALTER privilege on the table
-   ALTER ANY TABLE system privilege
-   ALTER ANY OBJECT system privilege

To create a trigger on a view owned by someone else, requires one of:

-   CREATE ANY TRIGGER system privilege
-   CREATE ANY OBJECT system privilege

Additionally, you must have one of the following privileges:

-   ALTER ANY VIEW system privilege
-   ALTER ANY OBJECT system privilege

To replace an existing trigger, you must be the owner of the table the trigger is built on, or have one of the following:

-   CREATE ANY TRIGGER system privilege
-   ALTER ANY OBJECT system privileges
-   ALTER ANY TRIGGER system privileges

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



## Side Effects

Automatic commit.



## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

CREATE TRIGGER is part of optional ANSI/ISO SQL Language Feature T211 "Basic trigger capability". Row triggers are optional ANSI/ISO SQL Language Feature T212, while INSTEAD OF triggers are optional ANSI/ISO SQL Language Feature T213.

Some trigger features in the software are not in the standard. These include:

-   The optional OR REPLACE syntax. If an existing trigger is replaced, authorization of the creation of the new trigger instance is bypassed.

-   The ORDER clause. In the ANSI/ISO SQL Standard, triggers are fired in the order they were created.

-   RESOLVE triggers.




</dd><dt><b>

Transact-SQL

</b></dt>
<dd>

ROW and RESOLVE triggers are not supported by Adaptive Server Enterprise. The data lake Relational Engine Transact-SQL dialect does not support Transact-SQL INSTEAD OF triggers, though these are supported by Adaptive Server Enterprise. Transact-SQL triggers are defined using different syntax.



</dd>
</dl>



This example creates a statement-level trigger. First, create a table as shown in this CREATE TABLE statement \(requires the CREATE TABLE system privilege\):

```
CREATE TABLE t0
( id INTEGER NOT NULL,
 times TIMESTAMP NULL DEFAULT CURRENT TIMESTAMP,
 remarks TEXT NULL,
 PRIMARY KEY ( id )
);
```

Next, create a statement-level trigger for this table:

```
CREATE TRIGGER myTrig AFTER INSERT ORDER 4 ON t0
REFERENCING NEW AS new_name
FOR EACH STATEMENT
BEGIN
  DECLARE @id1 INTEGER;
  DECLARE @times1 TIMESTAMP;
  DECLARE @remarks1 LONG VARCHAR;
  DECLARE @err_notfound EXCEPTION FOR SQLSTATE VALUE '02000';
//declare a cursor for table new_name
  DECLARE new1 CURSOR FOR
   SELECT id, times, remarks FROM new_name;
  OPEN new1;
 //Open the cursor, and get the value
  LoopGetRow:
  LOOP
      FETCH NEXT new1 INTO @id1, @times1,@remarks1;
      IF SQLSTATE = @err_notfound THEN
   LEAVE LoopGetRow
      END IF;
      //print the value or for other use
      PRINT (@remarks1);
  END LOOP LoopGetRow;
  CLOSE new1
END;
```

The following example replaces the myTrig trigger created in the previous example.

```
CREATE OR REPLACE TRIGGER myTrig AFTER INSERT ORDER 4 ON t0
REFERENCING NEW AS new_name
FOR EACH STATEMENT
BEGIN
FOR L1 AS new1 CURSOR FOR
   SELECT id, times, remarks FROM new_name
DO
     //print the value or for other use
     PRINT (@remarks1);
END FOR;
END;
```

The next example shows how you can use REFERENCING NEW in a BEFORE UPDATE trigger. This example ensures that postal codes in the new Employees table are in uppercase. You must have the SELECT, ALTER, and UPDATE object-level privileges on GROUPO.Employees to execute this statement:

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

UPDATE GROUPO.Employees SET state='ON', PostalCode='n2x 4y7' WHERE EmployeeID=191;
SELECT PostalCode FROM GROUPO.Employees WHERE EmployeeID = 191;
```

The next example shows how you can use REFERENCING OLD in a BEFORE DELETE trigger. This example prevents deleting an employee from the Employees table who has not been terminated.

```
CREATE TRIGGER TR_check_delete_employee 
BEFORE DELETE
ON Employees
REFERENCING OLD AS current_employee
FOR EACH ROW WHEN ( current_employee.Terminate IS NULL )
BEGIN
    RAISERROR 30001 'You cannot delete an employee who has not been fired';
END;
```

The next example shows how you can use REFERENCING NEW and REFERENCING OLD in a BEFORE UPDATE trigger. This example prevents a decrease in an employee's salary.

```
CREATE TRIGGER TR_check_salary_decrease 
    BEFORE UPDATE
      ON GROUPO.Employees
    REFERENCING OLD AS before_update 
    NEW AS after_update 
FOR EACH ROW 
BEGIN
   IF after_update.salary < before_update.salary THEN
    RAISERROR 30002 'You cannot decrease a salary';
    END IF;
END;
```

The next example shows how you can use REFERENCING NEW in a BEFORE INSERT and UPDATE trigger. The following example creates a trigger that fires before a row in the SalesOrderItems table is inserted or updated.

```
CREATE TRIGGER TR_update_date 
   BEFORE INSERT, UPDATE
     ON GROUPO.SalesOrderItems
   REFERENCING NEW AS new_row
FOR EACH ROW 
BEGIN
   SET new_row.ShipDate = CURRENT TIMESTAMP;
END;
```

The following trigger displays a message on the *History* tab of the Interactive SQL *Results* pane showing which action caused the trigger to fire.

```
CREATE TRIGGER tr BEFORE INSERT, UPDATE, DELETE
ON sample_table
REFERENCING OLD AS t1old
FOR EACH ROW
BEGIN
    DECLARE msg varchar(255);
    SET msg = 'This trigger was fired by an ';
    IF INSERTING THEN
        SET msg = msg || 'insert'
    ELSEIF DELETING THEN
        set msg = msg || 'delete'
    ELSEIF UPDATING THEN
        set msg = msg || 'update'
    END IF;
    MESSAGE msg TO CLIENT
END;
```

**Related Information**  


[ALTER TRIGGER Statement for Data Lake Relational Engine](alter-trigger-statement-for-data-lake-relational-engine-3be445c.md "Replaces a trigger definition with a modified version. You must include the entire new trigger definition in the ALTER TRIGGER statement. This statement applies to data lake Relational Engine catalog store tables only.")

[DROP TRIGGER Statement for Data Lake Relational Engine](drop-trigger-statement-for-data-lake-relational-engine-3be4974.md "Removes a trigger from the database. This statement applies to data lake Relational Engine catalog store tables only.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

