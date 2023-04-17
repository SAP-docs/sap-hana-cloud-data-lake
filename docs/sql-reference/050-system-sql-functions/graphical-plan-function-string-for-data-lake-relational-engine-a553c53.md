<!-- loioa553c53a84f21015b601a68bb24731e3 -->

# GRAPHICAL\_PLAN Function \[String\] for Data Lake Relational Engine

Returns the graphical query plan to Interactive SQL in an XML format string.



```
GRAPHICAL_PLAN ( <string-expression> 
[, <statistics-level>
[, <cursor-type>
[, <update-status> ]]])
```



<a name="loioa553c53a84f21015b601a68bb24731e3__iq_refbb_560"/>

## Parameters

 *<string-expression\>*
 :   SQL statement for which the plan is to be generated. string-expression is generally a SELECT statement, but it can also be an UPDATE or DELETE, INSERT SELECT, or SELECT INTO statement.

  *<statistics-level\>*
 :   An integer. Statistics-level can be:

    -   0 – Optimizer estimates only \(default\).
    -   2 – Detailed statistics including node statistics.
    -   3 – Detailed statistics.

  *<cursor-type\>*
 :   A cursor type, expressed as a string. Possible values are: asensitive, insensitive, sensitive, or keyset-driven. If cursor-type is not specified, asensitive is used by default.

  *<update-status\>*
 :   A string parameter accepting one of the following values indicating how the optimizer should treat the given cursor:

    -   READ-ONLY – The cursor is read-only.
    -   READ-WRITE \(default\) – The cursor can be read or written to.

 

## Returns

LONG VARCHAR

> ### Note:  
> The result data type is a LONG VARCHAR. If you use GRAPHICAL\_PLAN in a SELECT INTO statement, you need to use CAST and set GRAPHICAL\_PLAN to the correct data type and size.



<a name="loioa553c53a84f21015b601a68bb24731e3__iq_refbb_562"/>

## Remarks

> ### Note:  
> CIS functional compensation performance considerations apply.

If you do not provide an argument to the GRAPHICAL\_PLAN function, the query plan is returned to you from the cache. If there is no query plan in the cache, then this message appears:

```
plan not available
```

The behavior of GRAPHICAL\_PLAN function is controlled by database options QUERY\_PLAN\_TEXT\_ACCESS and QUERY\_PLAN\_TEXT\_CACHING. If QUERY\_PLAN\_TEXT\_ACCESS is OFF \(the default\), then this message appears:

```
Plan not available. The database option QUERY_PLAN_TEXT_ACCESS is OFF
```

If a user needs access to the plan, a user with the SET ANY CUSTOMER SYSTEM OPTION system privilege needs to set option QUERY\_PLAN\_TEXT\_ACCESS for that user.

If QUERY\_PLAN\_TEXT\_ACCESS is ON, and the query plan for the string expression is available in the cache maintained on the server, the query plan from the cache is returned to you.

If the query plan is not available in the cache and you are authorized to view plans on the client, then a query plan with optimizer estimates \(query plan with NOEXEC option ON\) is generated and appears on the Interactive SQL client plan window.

When a user requests a query plan that has not yet been executed, the query plan is not available in the cache. Instead, a query plan with optimizer estimates is returned without QUERY\_PLAN\_AFTER\_RUN statistics.

You cannot access query plans for stored procedures using the GRAPHICAL\_PLAN function.

Users can view the query plan for cursors opened for data lake Relational Engine queries. A cursor is declared and opened using DECLARE CURSOR and OPEN CURSOR. To obtain the query plan for the most recently opened cursor, use:

```
SELECT GRAPHICAL_PLAN ( );
```

With the QUERY\_PLAN\_AFTER\_RUN option OFF, the plan appears after OPEN CURSOR or CLOSE CURSOR. However, if QUERY\_PLAN\_AFTER\_RUN is ON, CLOSE CURSOR must be executed before you request the plan.



<a name="loioa553c53a84f21015b601a68bb24731e3__iq_refbb_564"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa553c53a84f21015b601a68bb24731e3__iq_refbb_563"/>

## Examples

-   The following example passes a SELECT statement as a string parameter and returns the plan for executing the query. It saves the plan in the file `gplan.xml`:

    ```
    SELECT GRAPHICAL_PLAN ('SELECT * FROM Employees');OUTPUT to 'C:\gplan.xml' HEXADECIMAL ASIS quote '';
    ```

    > ### Note:  
    > If you use the OUTPUT statement’s HEXADECIMAL clause set to ASIS to get formatted plan output, the values of characters are written without any escaping, even if the value contains control characters. ASIS is useful for text that contains formatting characters such as tabs or carriage returns.

-   The following example returns the query plan from the cache, if available:

    ```
    SELECT GRAPHICAL_PLAN ( );
    ```


**Related Information**  


[CAST Function \[Data Type Conversion\] for Data Lake Relational Engine](cast-function-data-type-conversion-for-data-lake-relational-engine-a53996d.md "Returns the value of an expression converted to a supplied data type.")

