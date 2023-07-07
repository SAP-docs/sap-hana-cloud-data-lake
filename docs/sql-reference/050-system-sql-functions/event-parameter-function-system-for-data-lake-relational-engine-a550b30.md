<!-- loioa550b30084f2101589a4e542f28d5e1e -->

# EVENT\_PARAMETER Function \[System\] for Data Lake Relational Engine

Provides context information for event handlers.



```
EVENT_PARAMETER ( <context-name> )
```



<a name="loioa550b30084f2101589a4e542f28d5e1e__event_parameter_parm1"/>

## Parameters


<dl>
<dt><b>

*<context-name\>*

</b></dt>
<dd>

One of the preset strings. The strings are case-insensitive, and carry the following information:

-   ConnectionId – the connection ID, as returned by connection\_property\( 'id' \)
-   User – the user ID for the user that caused the event to be triggered.
-   EventName – the name of the event that has been triggered.
-   Executions – the number of times the event handler has been executed.
-   IQDBMainSpaceName
-   NumActive – the number of active instances of an event handler. This is useful if you want to limit an event handler so that only one instance executes at any given time.
-   TableName – the name of the table, for use with RemainingValues.
-   *<condition-name\>* – you can also access any of the valid *<condition-name\>* arguments to the EVENT\_CONDITION function from the EVENT\_PARAMETER function.



</dd>
</dl>



<a name="loioa550b30084f2101589a4e542f28d5e1e__event_parameter_returns1"/>

## Returns

VARCHAR



<a name="loioa550b30084f2101589a4e542f28d5e1e__event_parameter_remarks1"/>

## Remarks

To define an event and its associated handler, use the CREATE EVENT statement.

> ### Note:  
> CIS functional compensation performance considerations apply.



<a name="loioa550b30084f2101589a4e542f28d5e1e__event_parameter_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar

**Related Information**  


[CREATE EVENT Statement for Data Lake Relational Engine](../080-sql-statements/create-event-statement-for-data-lake-relational-engine-a617091.md "Defines an event and its associated handler for automating predefined actions. Also defines scheduled actions.")

[EVENT\_CONDITION Function \[System\] for Data Lake Relational Engine](event-condition-function-system-for-data-lake-relational-engine-a54fb34.md "Specifies when an event handler is triggered.")

[EVENT\_CONDITION\_NAME Function \[System\] for Data Lake Relational Engine](event-condition-name-function-system-for-data-lake-relational-engine-a550344.md "Can be used to list the possible parameters for EVENT_CONDITION.")

