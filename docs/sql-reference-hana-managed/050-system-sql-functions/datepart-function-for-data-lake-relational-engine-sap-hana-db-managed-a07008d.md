<!-- loioa07008d5cbc347329b60d52b3e243ed6 -->

# DATEPART Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns an integer value for the specified part of a date/time value.



```
DATEPART ( <date-part>, <date-expression> );
```



<a name="loioa07008d5cbc347329b60d52b3e243ed6__section_ww1_2dm_srb"/>

## Parameters


<dl>
<dt><b>

*<date-part\>*

</b></dt>
<dd>

The date part to be returned.



</dd><dt><b>

*<date-expression\>*

</b></dt>
<dd>

The date for which the part is to be returned. The date must contain the date-part field.



</dd>
</dl>



<a name="loioa07008d5cbc347329b60d52b3e243ed6__section_nvp_2dm_srb"/>

## Result Set

INT



<a name="loioa07008d5cbc347329b60d52b3e243ed6__section_t3d_fdm_srb"/>

## Remarks

The DATE, TIME, and DTTM indexes do not support some date parts \(Calyearofweek, Calweekofyear, Caldayofweek, Dayofyear, Millisecond, Microsecond\).



<a name="loioa07008d5cbc347329b60d52b3e243ed6__section_twp_fdm_srb"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loioa07008d5cbc347329b60d52b3e243ed6__section_hjr_gdm_srb"/>

## Examples

-   The following statement returns the value 5:

    ```
    SELECT DATEPART( MONTH, '1987/05/02' )
    FROM iq_dummy;
    ```

-   The following statement returns the value 722,001:

    ```
    SELECT DATEPART(MICROSECOND, '2009-11-10
    14:57:52.722001') FROM iq_dummy;
    ```

-   The following statement returns the value 777,777:

    ```
    SELECT DATEPART(MICROSECOND, '2000/07/07
    07:07:07.777777') FROM iq_dummy;
    ```

-   The following statement returns the value 33,189:

    ```
    SELECT DATEPART(MCS, '2009-11-03 11:10:42.033189')
    FROM iq_dummy;
    ```


**Related Information**  


[DATE\_FIRST\_DAY\_OF\_WEEK Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../040-database-options/date-first-day-of-week-option-for-data-lake-relational-engine-sap-hana-db-managed-7b332a7.md "Determines the first day of the week.")

[DATEPART Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a547b06f84f210158ab3bd499f292d99.html "Returns an integer value for the specified part of a date/time value.") :arrow_upper_right:

