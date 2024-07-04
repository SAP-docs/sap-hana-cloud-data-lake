<!-- loioaae6da55cdb5426d9b6a06e2c7e5b2b4 -->

# DOW Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a number from 1 to 7 representing the day of the week of the specified date, with Sunday=1, Monday=2, and so on.



```
DOW ( <date-expression> );
```



<a name="loioaae6da55cdb5426d9b6a06e2c7e5b2b4__section_i5n_1zl_srb"/>

## Parameters


<dl>
<dt><b>

*<date-expression\>*

</b></dt>
<dd>

The date.



</dd>
</dl>



<a name="loioaae6da55cdb5426d9b6a06e2c7e5b2b4__section_frc_bzl_srb"/>

## Result Set

SMALLINT



<a name="loioaae6da55cdb5426d9b6a06e2c7e5b2b4__section_h1q_bzl_srb"/>

## Remarks

Use the DATE\_FIRST\_DAY\_OF\_WEEK option if you need Monday \(or another day\) to be the first day of the week.



<a name="loioaae6da55cdb5426d9b6a06e2c7e5b2b4__section_zcl_fm3_wrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioaae6da55cdb5426d9b6a06e2c7e5b2b4__section_kyx_fm3_wrb"/>

## Examples

The following statement returns the value 5:

```
SELECT DOW( '1998-07-09' ) FROM iq_dummy;
```

**Related Information**  


[DATE\_FIRST\_DAY\_OF\_WEEK Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../040-database-options/date-first-day-of-week-option-for-data-lake-relational-engine-sap-hana-db-managed-7b332a7.md "Determines the first day of the week.")

[DOW Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a54e817784f21015bfbbc50ea9eaecba.html "Returns a number from 1 to 7 representing the day of the week of the specified date, with Sunday=1, Monday=2, and so on.") :arrow_upper_right:

