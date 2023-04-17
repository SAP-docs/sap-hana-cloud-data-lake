<!-- loio3be445c66c5f10148227bf899726c725 -->

# ALTER TRIGGER Statement for Data Lake Relational Engine

Replaces a trigger definition with a modified version. You must include the entire new trigger definition in the ALTER TRIGGER statement.This statement applies to data lake Relational Engine catalog store tables only. 



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



 Syntax 1 - Change the definition of a trigger
 :   ```
ALTER TRIGGER <trigger-name> 
   [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <trigger-type> (varname]
   { [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <trigger-event> (varname][, ...  ] | [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/emph
     {"keyword"}) UPDATE OF (emph] [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <column-name> (varname][, ...] }
   [ [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/emph
     {"keyword"}) ORDER (emph] [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <integer> (varname] ] [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/emph
     {"keyword"}) ON (emph] [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <table-name> (varname]
   [ [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/emph
     {"keyword"}) REFERENCING (emph] [ [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/emph
     {"keyword"}) OLD AS (emph] [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <old-name> (varname] ]
      [ [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/emph
     {"keyword"}) NEW AS (emph] [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <new-name> (varname] ] 
      [ [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/emph
     {"keyword"}) REMOTE AS (emph] [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <remote-name> (varname] ] ]
   [ [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/emph
     {"keyword"}) FOR EACH (emph] { [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/emph
     {"keyword"}) ROW (emph] | [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/emph
     {"keyword"}) STATEMENT (emph] } ]
   [ [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/emph
     {"keyword"}) WHEN ( (emph] [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <search-condition> (varname] [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/emph
     {"keyword"}) ) (emph] ]
[/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <trigger-body> (varname]
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

  Syntax 2 - Obfuscate a trigger definition
 :   ```
ALTER TRIGGER <trigger-name> ON [<owner.>] <table-name> SET HIDDEN
```

 

<a name="loio3be445c66c5f10148227bf899726c725__section_l3q_l3f_xvb"/>

## Parameters

  *<trigger-type\>* 
 :   Row-level triggers can be defined to execute BEFORE, AFTER, or INSTEAD OF an insert, update, or delete operation. Statement-level triggers can be defined to execute INSTEAD OF or AFTER the statement.

    BEFORE UPDATE triggers fire any time an UPDATE occurs on a row, whenever the new value differs from the old value. That is, if a *<column-list\>* is specified for a BEFORE UPDATE trigger, then the trigger fires if any of the columns in *<column-list\>* appear in the SET clause of the UPDATE statement. If a *<column-list\>* is specified for an AFTER UPDATE trigger, then the trigger is fired only if the value of any of the columns in *<column-list\>* is *changed* by the UPDATE statement.

    INSTEAD OF triggers are the only form of trigger that you can define on a regular view. INSTEAD OF triggers replace the triggering action with another action. When an INSTEAD OF trigger fires, the triggering action is skipped and the specified action is performed. INSTEAD OF triggers can be defined as a row-level or a statement-level trigger. A statement-level INSTEAD OF trigger replaces the entire statement, including all row-level operations. If a statement-level INSTEAD OF trigger fires, then no row-level triggers fire as a result of that statement. However, the body of the statement-level trigger could perform other operations that, in turn, cause other row-level triggers to fire.

    If you are defining an INSTEAD OF trigger, then you cannot use the UPDATE OF *<column-list\>* clause, the ORDER clause, or the WHEN clause.

   *<trigger-event\>* 
 :   When defining a trigger, you can combine DELETE, INSERT, and UPDATE events in the same definition, but triggers for UPDATE OF events must be defined separately. You can define any number of DELETE, INSERT, and UPDATE triggers on a table. You can define any number of triggers for UPDATE OF events on a table, but only one per column.

    Triggers can be fired by the following events:

     DELETE event
     :   The trigger is invoked whenever one or more rows of the table are deleted.

      INSERT event
     :   The trigger is invoked whenever one or more rows are inserted into the table.

      UPDATE event
     :   The trigger is invoked whenever one or more rows of the table are updated.

        The keyword UPDATING is also supported for this clause for compatibility with other SQL dialects. The argument for UPDATING is a quoted string \(for example, `UPDATING( 'mycolumn' )`\), whereas the argument for UPDATE is an identifier \(for example, `UPDATE( mycolumn )`\).

      UPDATE OF *<column-list\>* event
     :   The trigger is invoked whenever a row of the associated table is updated and a column in the *<column-list\>* is modified. This type of trigger event cannot be used in a *<trigger-event-list\>*; it must be the only trigger event defined for the trigger. This clause cannot be used in an INSTEAD OF trigger.

        You can only specify one UPDATE OF trigger per column.

        You can write separate triggers for each event that you need to handle or, if you have some shared actions and some actions that depend on the event, you can create a trigger for all events and use an IF statement to distinguish the action taking place.

   ORDER clause
 :   It is good practice to specify order for triggers when defining multiple triggers on a table, even if they are not the same type. This ensures predictable results and makes easier to confirm which order they are processed in.

    When defining additional triggers of the same type \(insert, update, or delete\) to fire at the same time \(before, after, or resolve\), you must specify an ORDER clause to tell the database server the order in which to fire the triggers. Order numbers must be unique among same-type triggers configured to fire at the same time. If you specify an order number that is not unique, then an error is returned. Order numbers do not need to be in consecutive order \(for example, you could specify 1, 12, 30\). The database server fires the triggers starting with the lowest number.

    Typically, if you omit the ORDER clause, or specify 0, then the database server assigns the order of 1. However, if another same-type trigger is already set to 1, then an error is returned.

    When you create additional triggers that contain *multiple* event types, if you omit the ORDER clause, and one or more of the event types is the same as in other triggers \(for example, the *trigger-event-list* for one trigger is UPDATE, INSERT, and the *trigger-event-list* for another trigger is UPDATE\), the database server does not return an error. In this case, the database server processes the triggers in an implementation-specific order that may not be expected and is subject to change. Therefore, it is strongly recommended that you always specify an ORDER clause when defining more than one trigger on a table.

    When adding additional triggers, you may need to modify the existing same-type triggers for the event, depending on whether the actions of the triggers interact. If they do not interact, then the new trigger must have an ORDER value unique from other existing triggers. If they do interact, you need to consider what the other triggers do, and you may need to change the order in which they fire.

    The ORDER clause is not supported for INSTEAD OF triggers since there can only be one INSTEAD OF trigger of each type \(insert, update, or delete\) defined on a table or view.

  REFERENCING clause
 :   The REFERENCING OLD and REFERENCING NEW clauses allow you to refer to the inserted, deleted, or updated rows. With this clause an UPDATE is treated as a delete followed by an insert.

    An INSERT takes the REFERENCING NEW clause, which represents the inserted row. There is no REFERENCING OLD clause.

    A DELETE takes the REFERENCING OLD clause, which represents the deleted row. There is no REFERENCING NEW clause.

    An UPDATE takes the REFERENCING OLD clause, which represents the row before the update, and it takes the REFERENCING NEW clause, which represents the row after the update.

    The meanings of REFERENCING OLD and REFERENCING NEW differ, depending on whether the trigger is a row-level or a statement-level trigger. For row-level triggers, the REFERENCING OLD clause allows you to refer to the values in a row before an update or delete, and the REFERENCING NEW clause allows you to refer to the inserted or updated values. The OLD and NEW rows can be referenced in BEFORE and AFTER triggers. The REFERENCING NEW clause allows you to modify the new row in a BEFORE trigger before the insert or update operation takes place.

    For statement-level triggers, the REFERENCING OLD and REFERENCING NEW clauses refer to declared temporary tables holding the old and new values of the rows.

  FOR EACH clause
 :   To declare a trigger as a row-level trigger, use the FOR EACH ROW clause. To declare a trigger as a statement-level trigger, you can either use a FOR EACH STATEMENT clause or omit the FOR EACH clause. For clarity, it is recommended that you specify the FOR EACH STATEMENT clause if you are declaring a statement-level trigger.

  WHEN clause
 :   The trigger fires only for rows where the search-condition evaluates to true. The WHEN clause can be used only with row level triggers. This clause cannot be used in an INSTEAD OF trigger.

   *<trigger-body\>* 
 :   The trigger body contains the actions to take when the triggering action occurs, and consists of a BEGIN statement.

    You can include trigger operation conditions in the BEGIN statement. Trigger operation conditions perform actions depending on the trigger event that caused the trigger to fire. For example, if the trigger is defined to fire for both updates and deletes, you can specify different actions for the two conditions.

    You can also use Boolean conditions <code>{ INSERTING | DELETING | UPDATING [ ( '<i class="varname">&lt;col-name&gt;</i>' ) ] }</code> anywhere a condition can be used in the body of the trigger. This special syntax enables you to specify an additional action to take when performing some *<trigger-event\>*. For example, `IF INSERTING THEN SET msg = msg || 'insert'`.

  SET HIDDEN
 :   Hide the definition of the associated trigger and cause it to become unreadable.

    > ### Caution:  
    > The SET HIDDEN operation is irreversible.

 

## Remarks

For Syntax1, either the Transact-SQL or Watcom SQL form of the CREATE TRIGGER syntax can be used.



<a name="loio3be445c66c5f10148227bf899726c725__section_avv_xgz_m2b"/>

## Privileges

The privilege required varies by clause. 


<table>
<tr>
<th valign="top">

Clause



</th>
<th valign="top">

Privilege Name



</th>
</tr>
<tr>
<td valign="top">

Alter a trigger on a view



</td>
<td valign="top">

Requires one of:

-   You own the underlying table referenced by the trigger
-   ALTER ANY TRIGGER system privilege
-   ALTER ANY OBJECT system privilege
-   CREATE ANY OBJECT system privilege and ALTER object-level privilege on the underlying table



</td>
</tr>
<tr>
<td valign="top">

Alter a trigger on a materialized view



</td>
<td valign="top">

Requires one of:

-   You own the materialized view
-   ALTER ANY TRIGGER system privilege and ALTER ANY VIEW system privilege
-   ALTER ANY OBJECT system privilege



</td>
</tr>
</table>

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



## Side Effects

Automatic commit.



## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 **Related Information**  


[CREATE TRIGGER Statement for Data Lake Relational Engine](create-trigger-statement-for-data-lake-relational-engine-3be4860.md "Creates a trigger on a table. This statement applies to data lake Relational Engine catalog store tables only.")

[DROP TRIGGER Statement for Data Lake Relational Engine](drop-trigger-statement-for-data-lake-relational-engine-3be4974.md "Removes a trigger from the database. This statement applies to data lake Relational Engine catalog store tables only.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

