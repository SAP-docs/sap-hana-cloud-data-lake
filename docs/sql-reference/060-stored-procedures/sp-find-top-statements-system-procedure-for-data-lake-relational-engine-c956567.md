<!-- loioc95656706e1044c095af69e8a407420a -->

# sp\_find\_top\_statements System Procedure for Data Lake Relational Engine

Reports performance statistics for each logged statement and plan combination.



<a name="loioc95656706e1044c095af69e8a407420a__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_find_top_statements( <stmt_text>, <stmt_hash> );
```



## Parameters


<dl>
<dt><b>

*<stmt\_text\>* 

</b></dt>
<dd>

\(Optional\) A LONG VARCHAR parameter that specifies a SQL statement string. The default is NULL.



</dd><dt><b>

*<stmt\_hash\>* 

</b></dt>
<dd>

\(Optional\) An UNSIGNED BIGINT parameter that specifies a statement hash. The default is NULL.



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

*stmt\_hash*

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Returns the statement identifier.

</td>
</tr>
<tr>
<td valign="top">

*owner\_name*

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Returns the name of the owner of the stored procedure. The value is NULL if the statement isn't part of a stored procedure, user-defined function, trigger, or event. The value may also be NULL if the statement is executed as part of a stored procedure and the stored procedure is then dropped. A statement executed as part of a stored procedure gets a hash that is related to the procedure, not the statement text.

</td>
</tr>
<tr>
<td valign="top">

*proc\_name*

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Returns the name of the procedure that the statement belongs to. The value is NULL if the statement isn't part of a stored procedure, user-defined function, trigger, or event. The value may also be NULL if the statement is executed as part of a stored procedure and the stored procedure is then dropped. A statement executed as part of a stored procedure gets a hash that is related to the procedure, not the statement text.

</td>
</tr>
<tr>
<td valign="top">

*reusable\_stmt\_id*

</td>
<td valign="top">

UNSIGNED INTEGER

</td>
<td valign="top">

Returns a unique identifier assigned to the statement within a procedure \(not necessarily a line number\). The value is NULL if the statement isn't part of a stored procedure, user-defined function, trigger, or event.

</td>
</tr>
<tr>
<td valign="top">

*plan\_hash*

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Returns the plan identifier.

</td>
</tr>
<tr>
<td valign="top">

*max\_seconds*

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Returns the maximum runtime observed for the statement when executed with the current plan.

</td>
</tr>
<tr>
<td valign="top">

*sum\_runtime*

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Returns the total runtime for the statement with the current plan.

</td>
</tr>
<tr>
<td valign="top">

*sum\_square\_runtime*

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Returns the sum of the squares of the observed runtimes. This value is used for the standard deviation calculation.

</td>
</tr>
<tr>
<td valign="top">

*max\_blocking\_time*

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Returns the maximum observed blocking time for the statement when executed with the current plan.

</td>
</tr>
<tr>
<td valign="top">

*sum\_blocking\_time*

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Returns the total blocking time for the statement executions using the current plan.

</td>
</tr>
<tr>
<td valign="top">

*num\_exec*

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Returns the number of times the statement was executed using the current plan.

</td>
</tr>
<tr>
<td valign="top">

*total\_num\_rows*

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Returns the total number of rows returned or modified by the statement over all executions performed with the current plan.

</td>
</tr>
<tr>
<td valign="top">

*last\_max\_time\_utc*

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Returns the date and time in Coordinated Universal Time \(UTC\) that the maximum runtime was last updated.

</td>
</tr>
<tr>
<td valign="top">

*last\_time\_utc*

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Returns the date and time in Coordinated Universal Time \(UTC\) that the statement statistics were last updated with the current plan.

</td>
</tr>
<tr>
<td valign="top">

*temp\_space\_used\_mb*

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Temporary memory consumption in MB.

</td>
</tr>
<tr>
<td valign="top">

*cache\_page\_hit* 

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Number of pages found in the cache for the statement with the highest execution time.

</td>
</tr>
<tr>
<td valign="top">

*cache\_page\_miss*

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Number of pages not found in the cache for the statement with the highest execution time.

</td>
</tr>
<tr>
<td valign="top">

*max\_cpu\_usage\_perc*

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Highest CPU usage \(as percentage\) observed for the statement with the highest execution time.

</td>
</tr>
<tr>
<td valign="top">

*max\_num\_cpu*

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Maximum number of CPUs observed for the statement with the highest execution time.

</td>
</tr>
<tr>
<td valign="top">

*max\_thread\_count*

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Maximum number of active parallel threads for the statement with the highest execution time.

</td>
</tr>
<tr>
<td valign="top">

*max\_conn\_id*

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Connection ID of the statement with the highest execution time.

</td>
</tr>
<tr>
<td valign="top">

*max\_txn\_id*

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Transaction ID of the statement with the highest execution time.

</td>
</tr>
</table>



## Remarks

This procedure returns one or more rows for each logged statement, with each row indicating the execution plan that was used.

Specify the stmt\_text parameter if you want to see the hash for the specified statement, as well as the logged results for the statement, if any. If there's no data for the hash, a single row with hash and NULL is returned. If you want to fetch data for the statement and know the hash, specify the stmt\_hash parameter. Otherwise, don't specify either parameter. Specifying both parameters concurrently isn't permitted by the server.

This system procedure returns all of the data collected by the server, unless you provide a parameter to refine the results. By viewing these statistics, you can identify irregularities that can explain slow running statements.

> ### Note:  
> If the list of returned statements is long, then it's possible that not all of the data has been captured because of space limitations.



## Privileges

Require all of:

-   EXECUTE object-level privilege on the procedure
-   MONITOR system privilege
-   MANAGE PROFILING system privilege



## Side Effects

None.



## Examples

This example uses the sp\_find\_top\_statements system procedure to return performance statistics for each logged statement and plan combination.

```
CALL sp_find_top_statements();
```


<table>
<tr>
<th valign="top">

stmt\_hash

</th>
<th valign="top">

owner\_name

</th>
<th valign="top">

proc\_name

</th>
<th valign="top">

reusable\_stmt\_id

</th>
<th valign="top">

plan\_hash

</th>
<th valign="top">

max\_seconds

</th>
<th valign="top">

 

</th>
</tr>
<tr>
<td valign="top">

8825406443833030000

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

13335726911838300000

</td>
<td valign="top">

0.0099999997…

</td>
<td valign="top">

…

</td>
</tr>
<tr>
<td valign="top">

9223372054034640000

</td>
<td valign="top">

dbo

</td>
<td valign="top">

sp\_list\_mutexes\_semaphores

</td>
<td valign="top">

4

</td>
<td valign="top">

16856559335332700000

</td>
<td valign="top">

0.0099999997…

</td>
<td valign="top">

…

</td>
</tr>
<tr>
<td valign="top">

9223372099131800000

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

4011848611646360000

</td>
<td valign="top">

0.0199999999…

</td>
<td valign="top">

…

</td>
</tr>
<tr>
<td valign="top">

9223372058329610000

</td>
<td valign="top">

dbo

</td>
<td valign="top">

sa\_materialized\_view\_info

</td>
<td valign="top">

5

</td>
<td valign="top">

8698197228441170000

</td>
<td valign="top">

0

</td>
<td valign="top">

…

</td>
</tr>
<tr>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
</tr>
</table>

The example returns performance statistics for each logged statement that has both of the statements logged:

```
SELECT * 
FROM sp_find_top_statements( ) TS
INNER JOIN SYS.GTSYSPERFCACHESTMT PS ON TS.stmt_hash = PS.stmt_hash
ORDER BY TS.stmt_hash;
```

For all data, use OUTER JOIN.

The following query returns diagnostic information related to the execution of SQL statement:

```
SELECT * FROM <table_name> WHERE COL1>20;
```

```
CALL sp_find_top_statements('SELECT * FROM <table_name> WHERE COL1>20');
```

