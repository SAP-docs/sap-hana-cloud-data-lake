<!-- loioa58dbf3184f21015b67ac2deee9f7081 -->

# USER\_NAME Function \[System\] for Data Lake Relational Engine

Returns the user name.



```
USER_NAME ( [ <user-id> ] );
```



<a name="loioa58dbf3184f21015b67ac2deee9f7081__iq_refbb_1290"/>

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
> The result data type is a `LONG VARCHAR`. If you use `USER_NAME` in a `SELECT INTO` statement, you must use `CAST` and set `USER_NAME` to the correct data type and size.



<a name="loioa58dbf3184f21015b67ac2deee9f7081__iq_refbb_1293"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – SAP Adaptive Server Enterprise function implemented for data lake Relational Engine. In SAP ASE, USER\_NAME returns the user name, not the server user name.



<a name="loioa58dbf3184f21015b67ac2deee9f7081__iq_refbb_1292"/>

## Examples

-   The following statement returns the value “HDLADMIN”:

    ```
    SELECT USER_NAME ( 1 ) FROM iq_dummy;
    ```

-   The following statement returns the value “SYS”:

    ```
    SELECT USER_NAME ( 0 ) FROM iq_dummy;
    ```


**Related Information**  


[SUSER\_ID Function \[System\] for Data Lake Relational Engine](suser-id-function-system-for-data-lake-relational-engine-a5892d8.md "Returns an integer user identification number.")

[SUSER\_NAME Function \[System\] for Data Lake Relational Engine](suser-name-function-system-for-data-lake-relational-engine-a589ad8.md "Returns the user name.")

[USER\_ID Function \[System\] for Data Lake Relational Engine](user-id-function-system-for-data-lake-relational-engine-a58d3ba.md "Returns an integer user identification number.")

