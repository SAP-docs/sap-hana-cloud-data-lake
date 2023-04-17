<!-- loio3be2b72d6c5f1014aa53d553182330d6 -->

# ODBC Escape Syntax

You can use ODBC escape syntax from any ODBC application. This escape syntax allows you to call a set of common functions regardless of the database management system you are using.

> ### Note:  
> If you do not use escape syntax, then turn off escape syntax parsing in your ODBC application by setting the NOSCAN statement attribute. This improves performance by stopping the ODBC driver from scanning all SQL statements before sending them to the database server for execution. The following statement sets the NOSCAN statement attribute:
> 
> ```
> SQLSetStmtAttr ( hstmt, SQL_ATTR_NOSCAN, (SQLPOINTER) SQL_NOSCAN_ON, SQL_IS_UINTEGER );
> ```

The general form for the escape syntax is:

```
{ keyword <parameters> }
```

The set of keywords includes the following:

 \{d date-string\}
 :   The date string is any date value accepted by the database server.

  \{t time-string\}
 :   The time string is any time value accepted by the database server.

  \{ts date-string time-string\}
 :   The date/time string is any timestamp value accepted by the database server.

  \{guid uuid-string\}
 :   The uuid-string is any valid GUID string, for example, 41dfe9ef-db91-11d2-8c43-006008d26a6f.

  \{oj outer-join-expr\}
 :   The outer-join-expr is a valid OUTER JOIN expression accepted by the database server.

  \{? = call func\(p1, ...\)\}
 :   The function is any valid function call accepted by the database server.

  \{call proc\(p1, ...\)\}
 :   The procedure is any valid stored procedure call accepted by the database server.

  \{fn func\(p1, ...\)\}
 :   The function is any one of the library of functions listed below.

 You can use the escape syntax to access a library of functions implemented by the ODBC driver that includes number, string, time, date, and system functions.

For example, to obtain the current date in a database management system-neutral way, you would execute the following:

```
SELECT { FN CURDATE() }
```

The following tables list the functions that are supported by the ODBC driver.



## ODBC Driver Supported Functions


<table>
<tr>
<th valign="top">

Numeric Functions



</th>
<th valign="top">

String Functions



</th>
<th valign="top">

System Functions



</th>
<th valign="top">

Time/Date Functions



</th>
</tr>
<tr>
<td valign="top">

ABS



</td>
<td valign="top">

ASCII



</td>
<td valign="top">

DATABASE



</td>
<td valign="top">

CURDATE



</td>
</tr>
<tr>
<td valign="top">

ACOS



</td>
<td valign="top">

BIT\_LENGTH



</td>
<td valign="top">

IFNULL



</td>
<td valign="top">

CURRENT\_DATE



</td>
</tr>
<tr>
<td valign="top">

ASIN



</td>
<td valign="top">

CHAR



</td>
<td valign="top">

USER



</td>
<td valign="top">

CURRENT\_TIME



</td>
</tr>
<tr>
<td valign="top">

ATAN



</td>
<td valign="top">

CHAR\_LENGTH



</td>
<td valign="top">

CONVERT



</td>
<td valign="top">

CURRENT\_TIMESTAMP



</td>
</tr>
<tr>
<td valign="top">

ATAN2



</td>
<td valign="top">

CHARACTER\_LENGTH



</td>
<td valign="top">

 



</td>
<td valign="top">

CURTIME



</td>
</tr>
<tr>
<td valign="top">

CEILING



</td>
<td valign="top">

CONCAT



</td>
<td valign="top">

 



</td>
<td valign="top">

DAYNAME



</td>
</tr>
<tr>
<td valign="top">

COS



</td>
<td valign="top">

DIFFERENCE



</td>
<td valign="top">

 



</td>
<td valign="top">

DAYOFMONTH



</td>
</tr>
<tr>
<td valign="top">

COT



</td>
<td valign="top">

INSERT



</td>
<td valign="top">

 



</td>
<td valign="top">

DAYOFWEEK



</td>
</tr>
<tr>
<td valign="top">

DEGREES



</td>
<td valign="top">

LCASE



</td>
<td valign="top">

 



</td>
<td valign="top">

DAYOFYEAR



</td>
</tr>
<tr>
<td valign="top">

EXP



</td>
<td valign="top">

LEFT



</td>
<td valign="top">

 



</td>
<td valign="top">

EXTRACT



</td>
</tr>
<tr>
<td valign="top">

FLOOR



</td>
<td valign="top">

LENGTH



</td>
<td valign="top">

 



</td>
<td valign="top">

HOUR



</td>
</tr>
<tr>
<td valign="top">

LOG



</td>
<td valign="top">

LOCATE



</td>
<td valign="top">

 



</td>
<td valign="top">

MINUTE



</td>
</tr>
<tr>
<td valign="top">

LOG10



</td>
<td valign="top">

LTRIM



</td>
<td valign="top">

 



</td>
<td valign="top">

MONTH



</td>
</tr>
<tr>
<td valign="top">

MOD



</td>
<td valign="top">

OCTET\_LENGTH



</td>
<td valign="top">

 



</td>
<td valign="top">

MONTHNAME



</td>
</tr>
<tr>
<td valign="top">

PI



</td>
<td valign="top">

POSITION



</td>
<td valign="top">

 



</td>
<td valign="top">

NOW



</td>
</tr>
<tr>
<td valign="top">

POWER



</td>
<td valign="top">

REPEAT



</td>
<td valign="top">

 



</td>
<td valign="top">

QUARTER



</td>
</tr>
<tr>
<td valign="top">

RADIANS



</td>
<td valign="top">

REPLACE



</td>
<td valign="top">

 



</td>
<td valign="top">

SECOND



</td>
</tr>
<tr>
<td valign="top">

RAND



</td>
<td valign="top">

RIGHT



</td>
<td valign="top">

 



</td>
<td valign="top">

TIMESTAMPADD



</td>
</tr>
<tr>
<td valign="top">

ROUND



</td>
<td valign="top">

RTRIM



</td>
<td valign="top">

 



</td>
<td valign="top">

TIMESTAMPDIFF



</td>
</tr>
<tr>
<td valign="top">

SIGN



</td>
<td valign="top">

SOUNDEX



</td>
<td valign="top">

 



</td>
<td valign="top">

WEEK



</td>
</tr>
<tr>
<td valign="top">

SIN



</td>
<td valign="top">

SPACE



</td>
<td valign="top">

 



</td>
<td valign="top">

YEAR



</td>
</tr>
<tr>
<td valign="top">

SQRT



</td>
<td valign="top">

SUBSTRING



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

TAN



</td>
<td valign="top">

UCASE



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

TRUNCATE



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
</tr>
</table>



## ODBC TIMESTAMPADD, TIMESTAMPDIFF

The ODBC driver maps the TIMESTAMPADD and TIMESTAMPDIFF functions to the corresponding database server DATEADD and DATEDIFF functions. The syntax for the TIMESTAMPADD and TIMESTAMPDIFF functions is as follows.

```
{ fn TIMESTAMPADD( <interval>, <integer-expr>, <timestamp-expr> ) }
```

Returns the timestamp calculated by adding *<integer-expr\>* intervals of type *<interval\>* to *<timestamp-expr\>*. Valid values of *<interval\>* are shown below.

```
{ fn TIMESTAMPDIFF( <interval>, <timestamp-expr1>, <timestamp-expr2> ) }
```

Returns the integer number of intervals of type *<interval\>* by which *<timestamp-expr2\>* is greater than *<timestamp-expr1\>*. Valid values of *<interval\>* are shown below.


<table>
<tr>
<th valign="top">

interval



</th>
<th valign="top">

DATEADD/DATEDIFF Date-Part Mapping



</th>
</tr>
<tr>
<td valign="top">

SQL\_TSI\_YEAR



</td>
<td valign="top">

YEAR



</td>
</tr>
<tr>
<td valign="top">

SQL\_TSI\_QUARTER



</td>
<td valign="top">

QUARTER



</td>
</tr>
<tr>
<td valign="top">

SQL\_TSI\_MONTH



</td>
<td valign="top">

MONTH



</td>
</tr>
<tr>
<td valign="top">

SQL\_TSI\_WEEK



</td>
<td valign="top">

WEEK



</td>
</tr>
<tr>
<td valign="top">

SQL\_TSI\_DAY



</td>
<td valign="top">

DAY



</td>
</tr>
<tr>
<td valign="top">

SQL\_TSI\_HOUR



</td>
<td valign="top">

HOUR



</td>
</tr>
<tr>
<td valign="top">

SQL\_TSI\_MINUTE



</td>
<td valign="top">

MINUTE



</td>
</tr>
<tr>
<td valign="top">

SQL\_TSI\_SECOND



</td>
<td valign="top">

SECOND



</td>
</tr>
<tr>
<td valign="top">

SQL\_TSI\_FRAC\_SECOND



</td>
<td valign="top">

MICROSECOND - The DATEADD and DATEDIFF functions do not support a resolution of nanoseconds.



</td>
</tr>
</table>



## Interactive SQL

The ODBC escape syntax is identical to the JDBC escape syntax. In Interactive SQL, which uses JDBC, the braces *must* be doubled. There must not be a space between successive braces: "\{\{" is acceptable, but "\{ \{" is not. As well, you cannot use newline characters in the statement. The escape syntax cannot be used in stored procedures because they are not parsed by Interactive SQL.

For example, to obtain the number of weeks in February 2013, execute the following in Interactive SQL:

```
SELECT {{ fn TIMESTAMPDIFF(SQL_TSI_WEEK, '2013-02-01T00:00:00', '2013-03-01T00:00:00'  ) }}
```

