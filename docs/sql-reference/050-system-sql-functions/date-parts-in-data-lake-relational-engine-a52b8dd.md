<!-- loioa52b8dd384f210159bb4a3e3e02cb09f -->

# Date Parts in Data Lake Relational Engine

Many of the date functions use dates built from date parts.



This table displays allowed values of *<date-part\>*.


<table>
<tr>
<th valign="top">

Date Part



</th>
<th valign="top">

Abbreviation



</th>
<th valign="top">

Values



</th>
</tr>
<tr>
<td valign="top">

Year



</td>
<td valign="top">

yy



</td>
<td valign="top">

0001 – 9999



</td>
</tr>
<tr>
<td valign="top">

Quarter



</td>
<td valign="top">

qq



</td>
<td valign="top">

1 – 4



</td>
</tr>
<tr>
<td valign="top">

Month



</td>
<td valign="top">

mm



</td>
<td valign="top">

1 – 12



</td>
</tr>
<tr>
<td valign="top">

Week



</td>
<td valign="top">

wk



</td>
<td valign="top">

1 – 54



</td>
</tr>
<tr>
<td valign="top">

Day



</td>
<td valign="top">

dd



</td>
<td valign="top">

1 – 31



</td>
</tr>
<tr>
<td valign="top">

Dayofyear



</td>
<td valign="top">

dy



</td>
<td valign="top">

1 – 366



</td>
</tr>
<tr>
<td valign="top">

Weekday



</td>
<td valign="top">

dw



</td>
<td valign="top">

1 – 7 \(Sun. – Sat.\)



</td>
</tr>
<tr>
<td valign="top">

Hour



</td>
<td valign="top">

hh



</td>
<td valign="top">

0 – 23



</td>
</tr>
<tr>
<td valign="top">

Minute



</td>
<td valign="top">

mi



</td>
<td valign="top">

0 – 59



</td>
</tr>
<tr>
<td valign="top">

Second



</td>
<td valign="top">

ss



</td>
<td valign="top">

0 – 59



</td>
</tr>
<tr>
<td valign="top">

Millisecond



</td>
<td valign="top">

ms



</td>
<td valign="top">

0 – 999



</td>
</tr>
<tr>
<td valign="top">

Microsecond



</td>
<td valign="top">

mcs or us



</td>
<td valign="top">

0 – 999999



</td>
</tr>
<tr>
<td valign="top">

Calyearofweek



</td>
<td valign="top">

cyr



</td>
<td valign="top">

Integer. The year in which the week begins. The week containing the first few days of the year can be part of the last week of the previous year, depending upon which day it begins. If the new year starts on a Thursday through Saturday, its first week starts on the last Sunday of the previous year. If the new year starts on a Sunday through Wednesday, none of its days are part of the previous year.



</td>
</tr>
<tr>
<td valign="top">

Calweekofyear



</td>
<td valign="top">

cwk



</td>
<td valign="top">

An integer from 1 to 54 representing the week number within the year that contains the specified date.



</td>
</tr>
<tr>
<td valign="top">

Caldayofweek



</td>
<td valign="top">

cdw



</td>
<td valign="top">

The day number within the week \(Sunday = 1, Saturday = 7\).



</td>
</tr>
</table>



> ### Note:  
> By default, Sunday is the first day of the week. To make Monday the first day, use:
> 
> ```
> set option 'Date_First_Day_Of_Week' = '1'
> ```

**Related Information**  


[DATEADD Function \[Date and Time\] for Data Lake Relational Engine](dateadd-function-date-and-time-for-data-lake-relational-engine-a5449de.md "Returns the date produced by adding the specified number of the specified date parts to a date.")

[DATECEILING Function \[Date and Time\] for Data Lake Relational Engine](dateceiling-function-date-and-time-for-data-lake-relational-engine-a545210.md "Calculates a new date, time, or datetime value by increasing the provided value up to the nearest larger value of the specified granularity.")

[DATEDIFF Function \[Date and Time\] for Data Lake Relational Engine](datediff-function-date-and-time-for-data-lake-relational-engine-a545a63.md "Returns the interval between two dates.")

[DATEFLOOR Function \[Date and Time\] for Data Lake Relational Engine](datefloor-function-date-and-time-for-data-lake-relational-engine-a5462b6.md "Calculates a new date, time, or datetime value by reducing the provided value down to the nearest lower value of the specified multiple with the specified granularity.")

[DATENAME Function \[Date and Time\] for Data Lake Relational Engine](datename-function-date-and-time-for-data-lake-relational-engine-a5472b7.md "Returns the name of the specified part (such as the month “June”) of a date/time value, as a character string.")

[DATEPART Function \[Date and Time\] for Data Lake Relational Engine](datepart-function-date-and-time-for-data-lake-relational-engine-a547b06.md "Returns an integer value for the specified part of a date/time value.")

[DATEROUND Function \[Date and Time\] for Data Lake Relational Engine](dateround-function-date-and-time-for-data-lake-relational-engine-a5483a3.md "Calculates a new date, time, or datetime value by rounding the provided value up or down to the nearest multiple of the specified value with the specified granularity.")

