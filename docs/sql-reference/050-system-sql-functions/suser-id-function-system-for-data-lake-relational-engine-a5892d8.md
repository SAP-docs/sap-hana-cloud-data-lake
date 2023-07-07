<!-- loioa5892d8e84f21015ad62d1b43e0bae2e -->

# SUSER\_ID Function \[System\] for Data Lake Relational Engine

Returns an integer user identification number.



```
SUSER_ID ( [ <user-name> ] )
```



<a name="loioa5892d8e84f21015ad62d1b43e0bae2e__iq_refbb_1179"/>

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



<a name="loioa5892d8e84f21015ad62d1b43e0bae2e__iq_refbb_1182"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – SAP Adaptive Server Enterprise function implemented for data lake Relational Engine



<a name="loioa5892d8e84f21015ad62d1b43e0bae2e__iq_refbb_1181"/>

## Examples

-   The following statement returns the user identification number 1:

    ```
    SELECT SUSER_ID ('HDLADMIN') FROM iq_dummy
    ```

-   The following statement returns the user identification number 0:

    ```
    SELECT SUSER_ID ('SYS') FROM iq_dummy
    ```


**Related Information**  


[SUSER\_NAME Function \[System\] for Data Lake Relational Engine](suser-name-function-system-for-data-lake-relational-engine-a589ad8.md "Returns the user name.")

[USER\_ID Function \[System\] for Data Lake Relational Engine](user-id-function-system-for-data-lake-relational-engine-a58d3ba.md "Returns an integer user identification number.")

[USER\_NAME Function \[System\] for Data Lake Relational Engine](user-name-function-system-for-data-lake-relational-engine-a58dbf3.md "Returns the user name.")

