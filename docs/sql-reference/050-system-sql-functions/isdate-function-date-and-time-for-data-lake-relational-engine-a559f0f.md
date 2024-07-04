<!-- loioa559f0f684f21015b95ee838e6da62dc -->

# ISDATE Function \[Date and Time\] for Data Lake Relational Engine

Tests whether a string argument can be converted to a date.



```
ISDATE ( <string> );
```



<a name="loioa559f0f684f21015b95ee838e6da62dc__ISDATE_parm1"/>

## Parameters


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

The string to be analyzed to determine whether the string represents a valid date.



</dd>
</dl>



<a name="loioa559f0f684f21015b95ee838e6da62dc__ISDATE_returns1"/>

## Result Set

INT



<a name="loioa559f0f684f21015b95ee838e6da62dc__ISDATE_remarks1"/>

## Remarks

If a conversion is possible, the function returns 1; otherwise, it returns 0. If the argument is null, 0 is returned.



<a name="loioa559f0f684f21015b95ee838e6da62dc__ISDATE_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa559f0f684f21015b95ee838e6da62dc__ISDATE_examples1"/>

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


[ISDATE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/f28668e5060b4c6db2bc8832b9a5f4cd.html "Tests whether a string argument can be converted to a date.") :arrow_upper_right:

