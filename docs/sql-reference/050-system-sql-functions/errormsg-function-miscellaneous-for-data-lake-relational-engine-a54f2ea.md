<!-- loioa54f2ead84f210158668ce108de25460 -->

# ERRORMSG Function \[Miscellaneous\] for Data Lake Relational Engine

Provides the error message for the current error, or for a specified SQLSTATE or SQLCODE value.



```
ERRORMSG ( [ <sqlstate> | <sqlcode> ] );
```



<a name="loioa54f2ead84f210158668ce108de25460__ERRORMSG_parm1"/>

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



<a name="loioa54f2ead84f210158668ce108de25460__ERRORMSG_returns1"/>

## Result Set

A string containing the error message.

VARCHAR



<a name="loioa54f2ead84f210158668ce108de25460__ERRORMSG_remarks1"/>

## Remarks

If no argument is supplied, the error message for the current state is supplied. Any substitutions \(such as table names and column names\) are made.

If an argument is supplied, the error message for the supplied SQLSTATE or SQLCODE is returned, with no substitutions. Table names and column names are supplied as placeholders \('???'\).

The `ERRORMSG` function returns SAP SQL Anywhere and data lake Relational Engine error messages.



<a name="loioa54f2ead84f210158668ce108de25460__ERRORMSG_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa54f2ead84f210158668ce108de25460__ERRORMSG_example1"/>

## Example

The following statement returns the error message for SQLCODE -813:

```
select errormsg( -813 );
```

**Related Information**  


[ERRORMSG Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/fd7c8d326bf546a7a367bfca738c4357.html "Provides the error message for the current error, or for a specified SQLSTATE or SQLCODE value.") :arrow_upper_right:

