<!-- loio9533cea8d9b04beb9ed814b1a9ef641d -->

# TOLOCALTIME Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Converts a TIMESTAMP WITH TIME ZONE value, or a TIMESTAMP value \(which is assumed to be in Coordinated Universal Time \(UTC\)\), to a timestamp value that corresponds to the server’s local time using the standard time or daylight saving time rules for the server’s locale.



```
TOLOCALTIME( <timestamp-expression> );
```



<a name="loio9533cea8d9b04beb9ed814b1a9ef641d__section_eg1_fjv_vrb"/>

## Parameters


<dl>
<dt><b>

*<timestamp-expression\>*

</b></dt>
<dd>

The TIMESTAMP WITH TIME ZONE or TIMESTAMP expression to be converted. The TIMESTAMP WITH TIME ZONE value is converted to UTC before determining the local time. A TIMESTAMP value is assumed to be in UTC.



</dd>
</dl>



<a name="loio9533cea8d9b04beb9ed814b1a9ef641d__section_bzm_fjv_vrb"/>

## Result Set

TIMESTAMP



<a name="loio9533cea8d9b04beb9ed814b1a9ef641d__section_t1v_fjv_vrb"/>

## Remarks

The TOLOCALTIME function accepts any supported TIMESTAMP or TIMESTAMP WITH TIME ZONE value. However, it’s intended to be used with date/time values that are recent since rules for daylight savings time have changed over the years for most locales that implemented daylight savings at one time or another.

The standard time/daylight savings time rules in effect on the specified date can be used for historical dates. For example, for servers running in North America, dates before 2007 may be converted using the standard time/daylight time rules in effect before the most recent change to the rules in 2007. Also, dates before 1970 may or may not use the correct daylight saving rules.

Similarly, future dates can be converted using current rules even if those rules don't apply when the date arrives. Dates that follow the current date can be subject to change. Some locales never implemented daylight savings time \(for example, China/Beijing Time UTC+8\) so conversion from UTC to local time is straightforward.

Note that a string literal value specified as an argument to the TOLOCALTIME function must be cast to a TIMESTAMP WITH TIME ZONE if that is what the string value represents. If it is not cast to a TIMESTAMP WITH TIME ZONE, it is converted to a TIMESTAMP as if the zone offset isn't present.



<a name="loio9533cea8d9b04beb9ed814b1a9ef641d__section_uxk_gjv_vrb"/>

## Examples



### Example 1

The following example assumes that the database server is running in the North American Eastern time zone and shows how daylight rules affect the outcome. The input values represent dates and times that are 1 hour ahead of UTC. The date and time are converted to UTC by subtracting 1 hour and then converted to Eastern time, using the Standard Time/Daylight Time rules for the North American Eastern time zone.

The first date occurs when Eastern Standard time is in effect \(5 hours behind UTC\). The second and third dates occur when Eastern Daylight time is in effect \(4 hours behind UTC\).

```
SELECT CAST('2019/02/09 21:26:45.6789+1:00' AS TIMESTAMP WITH TIME ZONE) AS CT, TOLOCALTIME( CT )
UNION ALL
SELECT CAST('2019/03/10 21:26:45.6789+1:00' AS TIMESTAMP WITH TIME ZONE) AS CT, TOLOCALTIME( CT )
UNION ALL
SELECT CAST('2019/08/09 21:26:45.6789+1:00' AS TIMESTAMP WITH TIME ZONE) AS CT, TOLOCALTIME( CT )
ORDER BY CT

CT,                                 TOLOCALTIME(CT)
'2019-02-09 21:26:45.678+01:00',    '2019-02-09 15:26:45.678'
'2019-03-10 21:26:45.678+01:00',    '2019-03-10 16:26:45.678'
'2019-08-09 21:26:45.678+01:00',    '2019-08-09 16:26:45.678'

```



### Example 2

The following example assumes that the database server is running in the North American Eastern time zone and shows how daylight rules affect the outcome. The input values represent dates and times that are 5 or 4 hours behind UTC. The date and time are converted to UTC by adding the zone offset and then converted to Eastern time, using the Standard Time/Daylight Time rules for the North American Eastern time zone.

The first date occurs when Eastern Standard time is in effect \(5 hours behind UTC\). The second and third dates occur when Eastern Daylight time is in effect \(4 hours behind UTC\). As a result, each local time result has the same time of day as the input value.

```
SELECT CAST('2019/02/09 21:26:45.6789-5:00' AS TIMESTAMP WITH TIME ZONE) AS ET, TOLOCALTIME( ET )
UNION ALL
SELECT CAST('2019/03/10 21:26:45.6789-4:00' AS TIMESTAMP WITH TIME ZONE) AS ET, TOLOCALTIME( ET )
UNION ALL
SELECT CAST('2019/08/09 21:26:45.6789-4:00' AS TIMESTAMP WITH TIME ZONE) AS ET, TOLOCALTIME( ET )
ORDER BY ET;
ET,                                 TOLOCALTIME(ET)
'2019-02-09 21:26:45.678-05:00',    '2019-02-09 21:26:45.678'
'2019-03-10 21:26:45.678-04:00',    '2019-03-10 21:26:45.678'
'2019-08-09 21:26:45.678-04:00',    '2019-08-09 21:26:45.678'

```



### Example 3

The following example assumes that the database server is running in the North American Eastern time zone and shows how daylight rules affect the outcome. The input value, a TIMESTAMP, is assumed to be in UTC. Since Eastern Daylight time \(4 hours behind UTC\) is in effect for the specified date, the local time result is 4 hours earlier.

```
SELECT CAST('2019/08/09 21:26:45.6789' AS TIMESTAMP) AS UT, TOLOCALTIME( UT );
UT,                          TOLOCALTIME(UT)
'2019-08-09 21:26:45.678',   '2019-08-09 17:26:45.678'

```

**Related Information**  


[TOLOCALTIME Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/b472502b94a84aa78fd78db19b985f66.html "Converts a TIMESTAMP WITH TIME ZONE value, or a TIMESTAMP value (which is assumed to be in Coordinated Universal Time (UTC)), to a timestamp value that corresponds to the server’s local time using the standard time or daylight saving time rules for the server’s locale.") :arrow_upper_right:

