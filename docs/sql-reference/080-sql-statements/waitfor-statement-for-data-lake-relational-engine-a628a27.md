<!-- loioa628a27784f210159b71d2c8007a65f9 -->

# WAITFOR Statement for Data Lake Relational Engine

Delays processing for the current connection for a specified amount of time or until a given time.



<a name="loioa628a27784f210159b71d2c8007a65f9__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
WAITFOR { DELAY <time_value> | TIME <time_value> }
   [ CHECK EVERY <integer> }
   [ AFTER MESSAGE BREAK ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa628a27784f210159b71d2c8007a65f9__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

DELAY

</b></dt>
<dd>

Processing is suspended for the given *<time\_value\>* interval.



</dd><dt><b>

TIME

</b></dt>
<dd>

Processing is suspended until the server time reaches the *<time\_value\>* specified.



</dd><dt><b>

*<time\_value\>*

</b></dt>
<dd>

String.



</dd><dt><b>

CHECK EVERY *<integer\>*

</b></dt>
<dd>

Controls how often the `WAITFOR` statement wakes up. By default, `WAITFOR` wakes up every 5 seconds. The value is in milliseconds, and the minimum value is 250milliseconds.



</dd><dt><b>

AFTER MESSAGE BREAK

</b></dt>
<dd>

The `WAITFOR` statement can be used to wait for a message from another connection. In most cases, when a message is received it is forwarded to the application that executed the `WAITFOR` statement and the `WAITFOR` statement continues to wait. If the AFTER MESSAGE BREAK clause is specified, when a message is received from another connection, the `WAITFOR` statement completes. The message text is not forwarded to the application, but it can be accessed by obtaining the value of the MessageReceived connection property.



</dd>
</dl>



<a name="loioa628a27784f210159b71d2c8007a65f9__IQ_Usage"/>

## Remarks

The `WAITFOR` statement wakes up periodically \(every 5 seconds by default\) to check if it has been canceled or if messages have been received. If neither of these has happened, the statement continues to wait.

If the current server time is greater than the time specified, processing is suspended until that time on the following day.

`WAITFOR` provides an alternative to the following statement, and might be useful for customers who choose not to enable Java in the database:

```
call java.lang.Thread.sleep( <time_to_wait_in_millisecs> )
```

In many cases, scheduled events are a better choice than using `WAITFOR TIME`, because scheduled events execute on their own connection.



<a name="loioa628a27784f210159b71d2c8007a65f9__IQ_Permissions"/>

## Privileges

None



<a name="loioa628a27784f210159b71d2c8007a65f9__IQ_Side_Effects"/>

## Side Effects

The implementation of this statement uses a worker thread while it is waiting. This uses up one of the threads specified by the -gn server command line option.



<a name="loioa628a27784f210159b71d2c8007a65f9__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – this statement is also implemented by SAP Adaptive Server Enterprise



<a name="loioa628a27784f210159b71d2c8007a65f9__IQ_Examples"/>

## Examples

-   The following example waits for three seconds:

    ```
    WAITFOR DELAY '00:00:03';
    ```

-   The following example waits for 0.5 seconds \(500 milliseconds\):

    ```
    WAITFOR DELAY '00:00:00:500';
    ```

-   The following example waits until 8 p.m.:

    ```
    WAITFOR TIME '20:00';
    ```


**Related Information**  


[CREATE EVENT Statement for Data Lake Relational Engine](create-event-statement-for-data-lake-relational-engine-a617091.md "Defines an event and its associated handler for automating predefined actions. Also defines scheduled actions.")

