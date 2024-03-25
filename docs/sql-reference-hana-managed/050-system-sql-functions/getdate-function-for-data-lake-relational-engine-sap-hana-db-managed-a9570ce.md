<!-- loioa9570cefd0aa4bbab7c30441ab636856 -->

# GETDATE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the current date and time.



```
GETDATE ();
```



<a name="loioa9570cefd0aa4bbab7c30441ab636856__section_cdy_jqg_trb"/>

## Result Set

TIMESTAMP



<a name="loioa9570cefd0aa4bbab7c30441ab636856__section_j2k_kqg_trb"/>

## Remarks

GETDATE is a Transact-SQL compatible data manipulation function.



<a name="loioa9570cefd0aa4bbab7c30441ab636856__section_z2x_kqg_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa9570cefd0aa4bbab7c30441ab636856__section_g5j_lqg_trb"/>

## Example

The following statement returns the system date and time:

```
SELECT GETDATE( ) FROM iq_dummy;
```

**Related Information**  


[GETDATE Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a553449784f21015aba2a0fc3f4ce78c.html "Returns the current date and time.") :arrow_upper_right:

