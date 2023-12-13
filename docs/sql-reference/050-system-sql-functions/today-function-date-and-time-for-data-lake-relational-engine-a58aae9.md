<!-- loioa58aae9284f21015a550a97595a91cc9 -->

# TODAY Function \[Date and Time\] for Data Lake Relational Engine

Returns the current date. This is the historical syntax for `CURRENT DATE`.



```
TODAY ( * );
```



<a name="loioa58aae9284f21015a550a97595a91cc9__TODAY_returns1"/>

## Result Set

DATE



<a name="loioa58aae9284f21015a550a97595a91cc9__TODAY_remarks1"/>

## Remarks

Each instance of the TODAY function in a request is evaluated at most once. Multiple instances of TODAY in the same request may or may not share the identical DATE value.



<a name="loioa58aae9284f21015a550a97595a91cc9__TODAY_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa58aae9284f21015a550a97595a91cc9__TODAY_example1"/>

## Example

The following statement returns the current day according to the system clock:

```
SELECT TODAY( * ) FROM iq_dummy;
```

**Related Information**  


[TODAY Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/1f010045110b4fbfaebefa285ec75b87.html "Returns the current date. This is the historical syntax for CURRENT DATE.") :arrow_upper_right:

