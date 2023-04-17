<!-- loio3bea12936c5f1014ab3693753eb66c8f -->

# SYSSCHEDULE System View for Data Lake Relational Engine

Each row in the SYSSCHEDULE system view describes a time at which an event is to fire, as specified by the SCHEDULE clause of CREATE EVENT. The underlying system table for this view is ISYSSCHEDULE.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




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

event\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The unique number assigned to each event.



</td>
</tr>
<tr>
<td valign="top">

sched\_name



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

The name associated with the schedule for the event.



</td>
</tr>
<tr>
<td valign="top">

recurring



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

Indicates if the schedule is repeating.



</td>
</tr>
<tr>
<td valign="top">

start\_time



</td>
<td valign="top">

TIME



</td>
<td valign="top">

The schedule start time.



</td>
</tr>
<tr>
<td valign="top">

stop\_time



</td>
<td valign="top">

TIME



</td>
<td valign="top">

The schedule stop time if BETWEEN was used.



</td>
</tr>
<tr>
<td valign="top">

start\_date



</td>
<td valign="top">

DATE



</td>
<td valign="top">

The first date on which the event is scheduled to execute.



</td>
</tr>
<tr>
<td valign="top">

days\_of\_week



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

A bit mask indicating the days of the week on which the event is scheduled:

-   x01 = Sunday
-   x02 = Monday
-   x04 = Tuesday
-   x08 = Wednesday
-   x10 = Thursday
-   x20 = Friday
-   x40 = Saturday



</td>
</tr>
<tr>
<td valign="top">

days\_of\_month



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

A bit mask indicating the days of the month on which the event is scheduled. Some examples include:

-   x01 = first day
-   x02 = second day
-   x40000000 = 31st day
-   x80000000 = last day of month



</td>
</tr>
<tr>
<td valign="top">

interval\_units



</td>
<td valign="top">

CHAR\(10\)



</td>
<td valign="top">

The interval unit specified by EVERY:

-   HH = hours
-   NN = minutes
-   SS = seconds



</td>
</tr>
<tr>
<td valign="top">

interval\_amt



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

The period specified by EVERY.



</td>
</tr>
</table>

