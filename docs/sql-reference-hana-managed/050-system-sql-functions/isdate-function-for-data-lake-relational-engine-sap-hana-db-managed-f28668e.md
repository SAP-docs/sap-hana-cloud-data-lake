<!-- loiof28668e5060b4c6db2bc8832b9a5f4cd -->

# ISDATE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Tests whether a string argument can be converted to a date.



```
ISDATE ( <string> );
```



<a name="loiof28668e5060b4c6db2bc8832b9a5f4cd__section_dng_4nh_trb"/>

## Parameters


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

The string to be analyzed to determine whether the string represents a valid date.



</dd>
</dl>



<a name="loiof28668e5060b4c6db2bc8832b9a5f4cd__section_d3v_4nh_trb"/>

## Result Set

INT



<a name="loiof28668e5060b4c6db2bc8832b9a5f4cd__section_qkh_pnh_trb"/>

## Remarks

If a conversion is possible, the function returns 1; otherwise, it returns 0. If the argument is null, 0 is returned.



<a name="loiof28668e5060b4c6db2bc8832b9a5f4cd__section_zsv_pnh_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loiof28668e5060b4c6db2bc8832b9a5f4cd__section_ept_qnh_trb"/>

## Examples

The following example tests whether the birth\_date column holds valid dates, returning invalid dates as NULL, and valid dates in date format:

```
select birth_date from MyData;
------------------------------
1990/32/89
0101/32/89
1990/12/09
```

```
select 
  case when isdate(birth_date)=0 then NULL
  else cast(birth_date as date) 
  end 
  from MyData;
------------------------------------
(NULL)
(NULL)
1990-12-09
```

**Related Information**  


[ISDATE Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a559f0f684f21015b95ee838e6da62dc.html "Tests whether a string argument can be converted to a date.") :arrow_upper_right:

