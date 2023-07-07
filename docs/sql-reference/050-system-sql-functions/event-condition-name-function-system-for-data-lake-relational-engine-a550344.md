<!-- loioa550344c84f21015b24ccfeb1382c210 -->

# EVENT\_CONDITION\_NAME Function \[System\] for Data Lake Relational Engine

Can be used to list the possible parameters for `EVENT_CONDITION`.



```
EVENT_CONDITION_NAME ( <integer> )
```



<a name="loioa550344c84f21015b24ccfeb1382c210__event_condition_name_parm1"/>

## Parameters


<dl>
<dt><b>

*<integer\>*

</b></dt>
<dd>

An integer that is greater than or equal to zero.



</dd>
</dl>



<a name="loioa550344c84f21015b24ccfeb1382c210__event_condition_name_returns1"/>

## Returns

VARCHAR



<a name="loioa550344c84f21015b24ccfeb1382c210__event_condition_name_remarks1"/>

## Remarks

You can use EVENT\_CONDITION\_NAME to obtain a list of all EVENT\_CONDITION arguments by looping over integers until the function returns NULL.

To define an event and its associated handler, use the CREATE EVENT statement.

> ### Note:  
> CIS functional compensation performance considerations apply.



<a name="loioa550344c84f21015b24ccfeb1382c210__event_condition_name_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar

**Related Information**  


[CREATE EVENT Statement for Data Lake Relational Engine](../080-sql-statements/create-event-statement-for-data-lake-relational-engine-a617091.md "Defines an event and its associated handler for automating predefined actions. Also defines scheduled actions.")

[EVENT\_CONDITION Function \[System\] for Data Lake Relational Engine](event-condition-function-system-for-data-lake-relational-engine-a54fb34.md "Specifies when an event handler is triggered.")

[EVENT\_PARAMETER Function \[System\] for Data Lake Relational Engine](event-parameter-function-system-for-data-lake-relational-engine-a550b30.md "Provides context information for event handlers.")

