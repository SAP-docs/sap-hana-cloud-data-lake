<!-- loio81fd67bc6ce2101497f0d65edc4451bd -->

# STACK\_TRACE Function \[Miscellaneous\] for Data Lake Relational Engine

Returns information about the stack trace for the current statement.



```
STACK_TRACE(
[ <stack-frames>
[, <detail-level>
[, <connection-id> ] ] ]
);
```



<a name="loio81fd67bc6ce2101497f0d65edc4451bd__STACK_TRACE_parm1"/>

## Parameters


<dl class="glossary">
<dt><b>

*<stack-frames\>*

</b></dt>
<dd>

Controls whether to include procedures, outer-statements, or both.


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

*<detail-level\>*

</b></dt>
<dd>

Controls the level of detail to include in the returned data.


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

*<connection-id\>*

</b></dt>
<dd>

Use the connection\_id option to filter the results returned to the specified connection ID.



</dd>
</dl>



<a name="loio81fd67bc6ce2101497f0d65edc4451bd__STACK_TRACE_returns1"/>

## Result Set

LONG VARCHAR representing the stack trace of the current statement.



<a name="loio81fd67bc6ce2101497f0d65edc4451bd__STACK_TRACE_remarks1"/>

## Remarks

The result contains lines of text delimited by line feed \(\\n\) characters. Each line of the returned value contains the qualified procedure name or batch type, followed by the line number of the statement. The last line of the returned value is not terminated by a line feed character. The first line of the stack trace represents the line where the function was invoked. If a compound statement is not part of a procedure, function, trigger, or event, then the type of batch \(watcom\_batch or tsql\_batch\) is returned instead of the procedure name.

This function returns line numbers as found in the proc\_defn column of the SYSPROCEDURE system table for the procedure. These line numbers might differ from those of the source definition used to create the procedure.

This function returns the same information as the sa\_stack\_trace system procedure.



<a name="loio81fd67bc6ce2101497f0d65edc4451bd__STACK_TRACE_standards1"/>

## Standards and Compatibility


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



## Example

The following example illustrates a procedure call stack trace:

```
CREATE OR REPLACE PROCEDURE proc3()
BEGIN
   DECLARE v INTEGER;
   SET v = 1;
   SELECT * FROM sa_split_list( STACK_TRACE('caller+procedure', 'stack+sql'), '\n' ); 
END;

CREATE OR REPLACE PROCEDURE proc2()
BEGIN
    CALL proc3();
END;

CREATE OR REPLACE PROCEDURE proc1()
BEGIN
    CALL proc2();
END;


CALL proc1();
```

Results:

```
line_num row_value       
-------------------------------------------------------------------------------------------------------------------------------- 
          1   "DBA"."proc3" : 5 : select sa_split_list.line_num,sa_split_list.row_value from sa_split_list(STACK_TRACE('caller+procedure','stack+sql'),'\x0A')                                                                                                                 
          2   "DBA"."proc2" : 3 : call proc3()                                                                                                                                                                                                                                 
          3   "DBA"."proc1" : 3 : call proc2()                                                                                                                                                                                                                                 
          4    call proc1(
```

**Related Information**  


[STACK_TRACE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/387c96c17c9141249abeff9a59d22ec4.html "Returns information about the stack trace for the current statement.") :arrow_upper_right:

