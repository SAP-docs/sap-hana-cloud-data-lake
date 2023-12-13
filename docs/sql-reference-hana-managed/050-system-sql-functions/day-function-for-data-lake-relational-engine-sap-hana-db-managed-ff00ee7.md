<!-- loioff00ee7be6544c12a1e279a814961857 -->

# DAY Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns an integer from 1 to 31 corresponding to the day of the month of the date specified.



```
DAY ( <date-expression> );
```



<a name="loioff00ee7be6544c12a1e279a814961857__section_cck_ybm_srb"/>

## Parameters


<dl>
<dt><b>

*<date-expression\>*

</b></dt>
<dd>

The date.



</dd>
</dl>



<a name="loioff00ee7be6544c12a1e279a814961857__section_hnz_ybm_srb"/>

## Result Set

SMALLINT



<a name="loioff00ee7be6544c12a1e279a814961857__section_rmn_zbm_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioff00ee7be6544c12a1e279a814961857__section_bhb_1cm_srb"/>

## Example

The following statement returns the value 12:

```
SELECT DAY( '2001-09-12' ) FROM iq_dummy;
```

**Related Information**  


[DAY Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a5493fe284f2101587fac052951c6f01.html "Returns an integer from 1 to 31 corresponding to the day of the month of the date specified.") :arrow_upper_right:

