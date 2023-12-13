<!-- loioa567dab684f21015b1ad9ffdb01bb91a -->

# NEXT\_CONNECTION Function \[System\] for Data Lake Relational Engine

Returns the next connection number, or the first connection if the parameter is NULL.



```
NEXT_CONNECTION ( { <connection-id> }, { <database-id> } );
```



<a name="loioa567dab684f21015b1ad9ffdb01bb91a__iq_refbb_789"/>

## Parameters


<dl>
<dt><b>

*<connection-id\>*

</b></dt>
<dd>

An integer, usually returned from a previous call to NEXT\_CONNECTION. If *<connection-id\>* is NULL, NEXT\_CONNECTION returns the most recent connection ID.



</dd><dt><b>

*<database-id\>*

</b></dt>
<dd>

An integer representing one of the databases on the current server. If you supply no *<database-id\>*, the current database is used. If you supply NULL, then NEXT\_CONNECTION returns the next connection regardless of database.



</dd>
</dl>



## Result Set

INT



<a name="loioa567dab684f21015b1ad9ffdb01bb91a__iq_refbb_791"/>

## Remarks

> ### Note:  
> CIS functional compensation performance considerations apply.

You can use NEXT\_CONNECTION to enumerate the connections to a database. To get the first connection, pass NULL; to get each subsequent connection, pass the previous return value. The function returns NULL when there are no more connections.

NEXT\_CONNECTION can be used to enumerate the connections to a database. Connection IDs are generally created in monotonically increasing order. This function returns the next connection ID in reverse order.

To get the connection ID value for the most recent connection, enter NULL as the *<connection-id\>*. To get the subsequent connection, enter the previous return value. The function returns NULL when there are no more connections in the order.

NEXT\_CONNECTION is useful if you want to disconnect all the connections created before a specific time. However, because NEXT\_CONNECTION returns the connection IDS in reverse order, connections made after the function is started are not returned. If you want to ensure that all connections are disconnected, prevent new connections from being created before you run NEXT\_CONNECTION.



<a name="loioa567dab684f21015b1ad9ffdb01bb91a__iq_refbb_792"/>

## Standards and Compatibility

SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loioa567dab684f21015b1ad9ffdb01bb91a__iq_refbb_793"/>

## Examples

-   The following statement returns an identifier for the first connection on the current database. The identifier is an integer value like 10:

    ```
    SELECT NEXT_CONNECTION( NULL );
    ```

-   The following statement returns a value like 5:

    ```
    SELECT NEXT_CONNECTION( 10 );
    ```

-   The following call returns the next connection ID in reverse order from the specified *<connection-id\>* on the current database:

    ```
    SELECT NEXT_CONNECTION( connection-id );
    ```

-   The following call returns the next connection ID in reverse order from the specified *<connection-id \>*\(regardless of database\):

    ```
    SELECT NEXT_CONNECTION( connection-id, NULL );
    ```

-   The following call returns the next connection ID in reverse order from the specified *<connection-id\>* on the specified database:

    ```
    SELECT NEXT_CONNECTION( connection-id, database-id );
    ```

-   The following call returns the first \(earliest\) connection \(regardless of database\):

    ```
    SELECT NEXT_CONNECTION( NULL, NULL );
    ```

-   The following call returns the first \(earliest\) connection on the specified database:

    ```
    SELECT NEXT_CONNECTION( NULL, database-id );
    ```


