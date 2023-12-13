<!-- loioa589ad8084f21015ab2eb0b0272e8c41 -->

# SUSER\_NAME Function \[System\] for Data Lake Relational Engine

Returns the user name.



```
SUSER_NAME ( [ <user-id> ] );
```



<a name="loioa589ad8084f21015ab2eb0b0272e8c41__iq_refbb_1184"/>

## Parameters


<dl>
<dt><b>

*<user-id\>*

</b></dt>
<dd>

The user identification number.



</dd>
</dl>



## Result Set

LONG VARCHAR

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `SUSER_NAME` in a `SELECT INTO` statement, you must use `CAST` and set `SUSER_NAME` to the correct data type and size.



<a name="loioa589ad8084f21015ab2eb0b0272e8c41__iq_refbb_1187"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – SAP Adaptive Server Enterprise function implemented for data lake Relational Engine. In SAP ASE, `SUSER_NAME` returns the server user name.



<a name="loioa589ad8084f21015ab2eb0b0272e8c41__iq_refbb_1186"/>

## Examples

-   The following statement returns the value HDLADMIN:

    ```
    SELECT SUSER_NAME ( 1 ) FROM iq_dummy;
    ```

-   The following statement returns the value SYS:

    ```
    SELECT SUSER_NAME ( 0 ) FROM iq_dummy;
    ```


**Related Information**  


[SUSER\_ID Function \[System\] for Data Lake Relational Engine](suser-id-function-system-for-data-lake-relational-engine-a5892d8.md "Returns an integer user identification number.")

[USER\_ID Function \[System\] for Data Lake Relational Engine](user-id-function-system-for-data-lake-relational-engine-a58d3ba.md "Returns an integer user identification number.")

[USER\_NAME Function \[System\] for Data Lake Relational Engine](user-name-function-system-for-data-lake-relational-engine-a58dbf3.md "Returns the user name.")

