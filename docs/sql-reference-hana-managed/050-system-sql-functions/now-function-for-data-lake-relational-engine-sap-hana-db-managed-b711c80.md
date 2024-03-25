<!-- loiob711c800f2a640d9a76cba57c849f3f4 -->

# NOW Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the current date and time. This is the historical syntax for `CURRENT TIMESTAMP`.



```
NOW ( * );
```



<a name="loiob711c800f2a640d9a76cba57c849f3f4__section_gzr_znn_vrb"/>

## Result Set

TIMESTAMP



<a name="loiob711c800f2a640d9a76cba57c849f3f4__section_vgc_14n_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loiob711c800f2a640d9a76cba57c849f3f4__section_rwv_14n_vrb"/>

## Example

The following statement returns the current date and time:

```
SELECT NOW(*) FROM iq_dummy;
```

**Related Information**  


[NOW Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a568dfde84f210159d57b7ca3bb6ca84.html "Returns the current date and time. This is the historical syntax for CURRENT TIMESTAMP.") :arrow_upper_right:

