<!-- loio9cfb28b6a7d31014b73afaae02950c27 -->

# sqlany\_fetched\_rows\(a\_sqlany\_stmt \*\) Method

Returns the number of rows fetched.



```
public sacapi_i32 sqlany_fetched_rows (a_sqlany_stmt * sqlany_stmt)
```



## Parameters

sqlany\_stmt
:   A statement prepared successfully using sqlany\_prepare\(\).



## Returns

The number of rows fetched or -1 on failure.



## Remarks

In general, the number of rows fetched is equal to the size specified by the sqlany\_set\_rowset\_size\(\) function. The exception is when there are fewer rows from the fetch position to the end of the result set than specified, in which case the number of rows fetched is smaller than the specified row set size. The function returns -1 if the last fetch was unsuccessful or if the statement has not been executed. The function returns 0 if the statement has been executed but no fetching has been done.

**Related Information**  


[sqlany\_bind\_column\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_data\_value \*\) Method](sqlany-bind-column-a-sqlany-stmt-sacapi-u32-a-sqlany-data-value-method-9cf5d42.md "Binds a user-supplied buffer as a result set column to the prepared statement.")

[sqlany\_fetch\_next\(a\_sqlany\_stmt \*\) Method](sqlany-fetch-next-a-sqlany-stmt-method-3bf59e2.md "Returns the next set of rows from the result set.")

[sqlany\_fetch\_absolute\(a\_sqlany\_stmt \*, sacapi\_i32\) Method](sqlany-fetch-absolute-a-sqlany-stmt-sacapi-i32-method-3bf5955.md "Moves the current row in the result set to the specified row number and then fetches rows of data starting from the current row.")

