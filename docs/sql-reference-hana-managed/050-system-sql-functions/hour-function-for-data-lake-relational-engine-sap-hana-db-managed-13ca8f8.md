<!-- loio13ca8f80a24a45b3ae7e434753dd97c8 -->

# HOUR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a number from 0 to 23 corresponding to the hour component of the specified date/time.



```
HOUR ( <datetime-expression> )
```



<a name="loio13ca8f80a24a45b3ae7e434753dd97c8__section_vc2_t4g_trb"/>

## Parameters


<dl>
<dt><b>

*<datetime-expression\>*

</b></dt>
<dd>

The date/time.



</dd>
</dl>



<a name="loio13ca8f80a24a45b3ae7e434753dd97c8__section_wwp_t4g_trb"/>

## Returns

SMALLINT



<a name="loio13ca8f80a24a45b3ae7e434753dd97c8__section_tvd_54g_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio13ca8f80a24a45b3ae7e434753dd97c8__section_g5w_54g_trb"/>

## Example

The following statement returns the value 21:

```
SELECT HOUR( '1998-07-09 21:12:13' ) FROM iq_dummy
```

**Related Information**  


[HOUR Function [Date and Time] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a55651ad84f210158eceac6470043938.html "Returns a number from 0 to 23 corresponding to the hour component of the specified date/time.") :arrow_upper_right:

