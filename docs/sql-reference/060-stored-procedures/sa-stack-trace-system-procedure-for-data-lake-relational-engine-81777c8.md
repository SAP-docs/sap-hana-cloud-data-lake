<!-- loio81777c8f6ce21014bdaf977b02167984 -->

# sa\_stack\_trace System Procedure for Data Lake Relational Engine

Returns the stack trace leading to the current call location.



<a name="loio81777c8f6ce21014bdaf977b02167984__section_p4t_vqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_stack_trace(
[ <stack_frames>
[, <detail_level>
[, <connection_id> ] ] ]
)
```



## Parameters


<dl>
<dt><b>

*<stack\_frames\>* 

</b></dt>
<dd>

Use this optional CHAR\(128\) parameter to specify one of the following:


<dl>
<dt><b>

'procedure'

</b></dt>
<dd>

Return procedures but not the outer-most statement. This is the default behavior.



</dd><dt><b>

'caller'

</b></dt>
<dd>

Return only the outer-most statement \(the statement that arrived from the client\).



</dd><dt><b>

'procedure+caller', 'caller+procedure'

</b></dt>
<dd>

Return all statements.



</dd>
</dl>



</dd><dt><b>

*<detail\_level\>* 

</b></dt>
<dd>

Use this optional CHAR\(128\) parameter to specify one of the following:


<dl>
<dt><b>

'stack'

</b></dt>
<dd>

Include procedure names and line numbers. This is the default behavior.



</dd><dt><b>

'stack+sql', 'sql+stack'

</b></dt>
<dd>

Include the procedure names and line numbers, as well as the SQL text of the statement being executed at each level.



</dd>
</dl>



</dd><dt><b>

*<connection\_id\>* 

</b></dt>
<dd>

Use this optional UNSIGNED INTEGER parameter to filter the results returned to the specified connection ID. If not specified, information for the current connection is returned.



</dd>
</dl>



## Result Set


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

StackLevel

</td>
<td valign="top">

UNSIGNED SMALLINT

</td>
<td valign="top">

The current line has Stack Level 1.

</td>
</tr>
<tr>
<td valign="top">

UserName

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the owner of the procedure or trigger, or NULL if the current level is in a batch.

</td>
</tr>
<tr>
<td valign="top">

ProcName

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the procedure or trigger where the call was performed or the batch type.

</td>
</tr>
<tr>
<td valign="top">

LineNumber

</td>
<td valign="top">

UNSIGNED INTEGER

</td>
<td valign="top">

The line number of the call within the procedure, trigger, or batch.

</td>
</tr>
<tr>
<td valign="top">

SQLStatement

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The statement being executed.

</td>
</tr>
</table>



## Remarks

Each record in the result set represents a single call on the stack. If the compound statement is not part of a procedure, function, trigger, or event, then the type of batch \(watcom\_batch or tsql\_batch\) is returned instead of the procedure name.

This function returns line numbers as found in the proc\_defn column of the SYSPROCEDURE system table for the procedure. These line numbers might differ from those of the source definition used to create the procedure.



## Privileges

You must have EXECUTE privilege on the system procedure.



## Side Effects

None.



## Example

This example shows how to obtain the result set columns from the sa\_stack\_trace system procedure:

```
SELECT StackLevel, UserName, ProcName, LineNumber FROM sa_stack_trace();
```

When this statement is executed outside of the context of a stored procedure, the result set is empty.

The following example shows the implementation of a general stack trace procedure that sends its results to the client window:

```
CREATE OR REPLACE PROCEDURE StackDump( MSG CHAR(128) )
BEGIN
    DECLARE myStackLevel UNSIGNED SMALLINT;
    DECLARE myUserName CHAR(128);
    DECLARE myProcName CHAR(128);
    DECLARE myLineNumber UNSIGNED SMALLINT;
    DECLARE mySQLStatement long varchar;
    DECLARE err_notfound
        EXCEPTION FOR SQLSTATE '02000';
    DECLARE myStack CURSOR FOR
        SELECT StackLevel, UserName, ProcName, LineNumber, SQLStatement FROM sa_stack_trace('caller+procedure', 'stack+sql');
    MESSAGE 'Stack Trace: ' || MSG TO CLIENT;
    OPEN myStack;
    StackLoop: LOOP
        FETCH NEXT myStack
            INTO myStackLevel, myUserName, myProcName, myLineNumber, mySQLStatement;
        IF SQLSTATE = err_notfound THEN
            LEAVE StackLoop;
        END IF;
        IF myStackLevel != 1 THEN
            MESSAGE myStackLevel - 1 || ' ' || myUserName || ' ' || myProcName || ' ' || myLineNumber || ' ' || mySQLStatement
                TO CLIENT;
        ENDIF
    END LOOP StackLoop;
    CLOSE myStack;
END;
 
CREATE OR REPLACE PROCEDURE Proc1()
BEGIN
    CALL Proc2();
END;
 
CREATE OR REPLACE PROCEDURE Proc2()
BEGIN
    CALL Proc3();
END;
 
CREATE OR REPLACE PROCEDURE Proc3()
BEGIN
    CALL StackDump('Snapshot from Proc3');
END;
 
CALL Proc1();

```

Results:

```
CALL Proc1();
-- Stack Trace: Snapshot from Proc3
-- 1 DBA proc3 3 call StackDump('Snapshot from Proc3')
-- 2 DBA proc2 3 call Proc3()
-- 3 DBA proc1 3 call Proc2()
-- Procedure completed
```

**Related Information**  


[STACK\_TRACE Function \[Miscellaneous\] for Data Lake Relational Engine](../050-system-sql-functions/stack-trace-function-miscellaneous-for-data-lake-relational-engine-81fd67b.md "Returns information about the stack trace for the current statement.")

