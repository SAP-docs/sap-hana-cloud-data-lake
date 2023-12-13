<!-- loioa5209f7084f21015a9229f74850f385b -->

# Retrieve Dates and Times in Data Lake Relational Engine

There are three ways in which you can retrieve dates and times from the database.



-   Using any interface, as a string

-   Using ODBC, as a TIMESTAMP structure

-   Using embedded SQL, as a SQLDATETIME structure


When a date or time is retrieved as a string, it’s retrieved in the format specified by the database options DATE\_FORMAT, TIME\_FORMAT, and TIMESTAMP\_FORMAT.

The following operators are allowed on dates:


<table>
<tr>
<th valign="top" rowspan="1">

Operator

</th>
<th valign="top" rowspan="1">

Description

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

timestamp + integer

</td>
<td valign="top" rowspan="1">

Add the specified number of days to a date or timestamp.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

timestamp - integer

</td>
<td valign="top" rowspan="1">

Subtract the specified number of days from a date or timestamp.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

date - date

</td>
<td valign="top" rowspan="1">

Compute the number of days between two dates or timestamps.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

date + time

</td>
<td valign="top" rowspan="1">

Create a timestamp combining the given date and time.

</td>
</tr>
</table>

