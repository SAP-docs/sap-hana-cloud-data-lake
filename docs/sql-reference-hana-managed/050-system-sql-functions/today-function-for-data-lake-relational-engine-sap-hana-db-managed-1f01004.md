<!-- loio1f010045110b4fbfaebefa285ec75b87 -->

# TODAY Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the current date. This is the historical syntax for `CURRENT DATE`.



```
TODAY ( * )
```



<a name="loio1f010045110b4fbfaebefa285ec75b87__section_zl5_mjv_vrb"/>

## Returns

DATE



<a name="loio1f010045110b4fbfaebefa285ec75b87__section_r4t_rjv_vrb"/>

## Remarks

Each instance of the TODAY function in a request is evaluated at most once. Multiple instances of TODAY in the same request may or may not share the identical DATE value.



<a name="loio1f010045110b4fbfaebefa285ec75b87__section_bhm_sjv_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio1f010045110b4fbfaebefa285ec75b87__section_gkz_sjv_vrb"/>

## Example

The following statement returns the current day according to the system clock:

```
SELECT TODAY( * ) FROM iq_dummy
```

**Related Information**  


[TODAY Function [Date and Time] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a58aae9284f21015a550a97595a91cc9.html "Returns the current date. This is the historical syntax for CURRENT DATE.") :arrow_upper_right:

