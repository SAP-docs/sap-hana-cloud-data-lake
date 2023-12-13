<!-- loio328e90f2bcb14535a8a34b74369bbbfc -->

# SIMILAR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns an integer between 0 and 100 representing the similarity between two strings.



```
SIMILAR ( <string-expression1>, <string-expression2> );
```



<a name="loio328e90f2bcb14535a8a34b74369bbbfc__section_jgh_5y5_vrb"/>

## Parameters


<dl>
<dt><b>

*<string-expression1\>*

</b></dt>
<dd>

The first string to be compared.



</dd><dt><b>

*<string-expression2\>*

</b></dt>
<dd>

The second string to be compared.



</dd>
</dl>



<a name="loio328e90f2bcb14535a8a34b74369bbbfc__section_c4t_5y5_vrb"/>

## Result Set

SMALLINT



<a name="loio328e90f2bcb14535a8a34b74369bbbfc__section_wqb_vy5_vrb"/>

## Remarks

The function returns an integer between 0 and 100 representing the similarity between the two strings. The result can be interpreted as the percentage of characters matched between the two strings. A value of 100 indicates that the two strings are identical.

This function can be used to correct a list of names \(such as customers\). Some customers might have been added to the list more than once with slightly different names. Join the table to itself and produce a report of all similarities greater than 90 percent but less than 100 percent.



<a name="loio328e90f2bcb14535a8a34b74369bbbfc__section_hvp_vy5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio328e90f2bcb14535a8a34b74369bbbfc__section_lzy_vy5_vrb"/>

## Example

The following statement returns the value 80:

```
SELECT SIMILAR( 'toast', 'coast' ) FROM iq_dummy;
```

This signifies that the two values are 80% similar.

**Related Information**  


[SIMILAR Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a57f56c484f21015b142b043da48dee3.html "Returns an integer between 0 and 100 representing the similarity between two strings.") :arrow_upper_right:

