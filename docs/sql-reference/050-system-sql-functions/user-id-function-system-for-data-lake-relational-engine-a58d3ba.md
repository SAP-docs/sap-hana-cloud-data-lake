<!-- loioa58d3bab84f2101590ac91b509c292c5 -->

# USER\_ID Function \[System\] for Data Lake Relational Engine

Returns an integer user identification number.



```
USER_ID ( [ <user-name> ] )
```



<a name="loioa58d3bab84f2101590ac91b509c292c5__iq_refbb_1285"/>

## Parameters


<dl>
<dt><b>

*<user-name\>*

</b></dt>
<dd>

The user name.



</dd>
</dl>



## Returns

INT



<a name="loioa58d3bab84f2101590ac91b509c292c5__iq_refbb_1288"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – SAP Adaptive Server Enterprise function implemented for data lake Relational Engine



<a name="loioa58d3bab84f2101590ac91b509c292c5__iq_refbb_1287"/>

## Examples

-   The following statement returns the user identification number 1:

    ```
    SELECT USER_ID ('HDLADMIN') FROM iq_dummy
    ```

-   The following statement returns the user identification number 0:

    ```
    SELECT USER_ID ('SYS') FROM iq_dummy
    ```


**Related Information**  


[SUSER\_ID Function \[System\] for Data Lake Relational Engine](suser-id-function-system-for-data-lake-relational-engine-a5892d8.md "Returns an integer user identification number.")

[SUSER\_NAME Function \[System\] for Data Lake Relational Engine](suser-name-function-system-for-data-lake-relational-engine-a589ad8.md "Returns the user name.")

[USER\_NAME Function \[System\] for Data Lake Relational Engine](user-name-function-system-for-data-lake-relational-engine-a58dbf3.md "Returns the user name.")

