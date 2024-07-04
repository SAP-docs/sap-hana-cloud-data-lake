<!-- loioe5839f4e21a9431984d1705f1691f2fa -->

# DATE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Converts the expression into a date, and removes any hours, minutes, or seconds.



```
DATE ( <expression> );
```



<a name="loioe5839f4e21a9431984d1705f1691f2fa__section_wgn_mgm_srb"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The value to be converted to date format. The expression is usually a string.



</dd>
</dl>



<a name="loioe5839f4e21a9431984d1705f1691f2fa__section_pnz_mgm_srb"/>

## Result Set

DATE



<a name="loioe5839f4e21a9431984d1705f1691f2fa__section_ncj_ngm_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioe5839f4e21a9431984d1705f1691f2fa__section_t4v_ngm_srb"/>

## Examples

The following statement returns the value 1988-11-26 as a date:

```
SELECT DATE( '1988-11-26 21:20:53' ) FROM iq_dummy;
```

**Related Information**  


[DATE Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a544131284f21015a70ed7c8e7db2f8b.html "Converts the expression into a date, and removes any hours, minutes, or seconds.") :arrow_upper_right:

