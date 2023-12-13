<!-- loiob6977f358a8549aab30b4f2c48dd3c83 -->

# DATENAME Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the name of the specified part \(such as the month “June”\) of a date/time value, as a character string.



```
DATEMNAME ( <date-part>, <date-expression> );
```



<a name="loiob6977f358a8549aab30b4f2c48dd3c83__section_q5c_sdm_srb"/>

## Parameters


<dl>
<dt><b>

*<date-part\>*

</b></dt>
<dd>

The date part to be named.



</dd><dt><b>

*<date-expression\>*

</b></dt>
<dd>

The date for which the date part name is to be returned. The date must contain the requested date-part.



</dd>
</dl>



<a name="loiob6977f358a8549aab30b4f2c48dd3c83__section_uvf_tdm_srb"/>

## Result Set

VARCHAR



<a name="loiob6977f358a8549aab30b4f2c48dd3c83__section_wlw_tdm_srb"/>

## Result Set

VARCHAR



<a name="loiob6977f358a8549aab30b4f2c48dd3c83__section_mxh_5dm_srb"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loiob6977f358a8549aab30b4f2c48dd3c83__section_dz5_5dm_srb"/>

## Examples

-   The following statement returns the value May:

    ```
    SELECT DATENAME( MONTH , '1987/05/02' )
    FROM iq_dummy;
    ```

-   The following statement returns the value 722,001:

    ```
    SELECT DATENAME(MICROSECOND, '2009-11-10
    14:57:52.722001') FROM iq_dummy;
    ```

-   The following statement returns the value 777,777:

    ```
    SELECT DATENAME(MICROSECOND, '2000/07/07
    07:07:07.777777') FROM iq_dummy;
    ```

-   The following statement returns the value 33,189:

    ```
    SELECT DATENAME(MCS, '2009-11-03 11:10:42.033189')
    FROM iq_dummy;
    ```


**Related Information**  


[DATENAME Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a5472b7084f21015892b91f8f67b6ef9.html "Returns the name of the specified part (such as the month “June”) of a date/time value, as a character string.") :arrow_upper_right:

