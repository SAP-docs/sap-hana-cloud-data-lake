<!-- loiofd7c8d326bf546a7a367bfca738c4357 -->

# ERRORMSG Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Provides the error message for the current error, or for a specified SQLSTATE or SQLCODE value.



```
ERRORMSG ( [ <sqlstate> | <sqlcode> ] );
```



<a name="loiofd7c8d326bf546a7a367bfca738c4357__section_gxk_psg_trb"/>

## Parameters


<dl>
<dt><b>

*<sqlstate\>*

</b></dt>
<dd>

String representing the SQLSTATE for which the error message is to be returned.



</dd><dt><b>

*<sqlcode\>*

</b></dt>
<dd>

Integer representing the SQLCODE for which the error message is to be returned.



</dd>
</dl>



<a name="loiofd7c8d326bf546a7a367bfca738c4357__section_k12_qsg_trb"/>

## Result Set

A string containing the error message.

VARCHAR



<a name="loiofd7c8d326bf546a7a367bfca738c4357__section_wqq_qsg_trb"/>

## Remarks

If no argument is supplied, the error message for the current state is supplied. Any substitutions \(such as table names and column names\) are made.

If an argument is supplied, the error message for the supplied SQLSTATE or SQLCODE is returned, with no substitutions. Table names and column names are supplied as placeholders \('???'\).

The `ERRORMSG` function returns SAP SQL Anywhere and data lake Relational Engine error messages.



<a name="loiofd7c8d326bf546a7a367bfca738c4357__section_nyh_rsg_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loiofd7c8d326bf546a7a367bfca738c4357__section_mcy_rsg_trb"/>

## Examples

The following statement returns the error message for SQLCODE -813:

```
select errormsg( -813 );
```

**Related Information**  


[ERRORMSG Function \[Miscellaneous\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a54f2ead84f210158668ce108de25460.html "Provides the error message for the current error, or for a specified SQLSTATE or SQLCODE value.") :arrow_upper_right:

