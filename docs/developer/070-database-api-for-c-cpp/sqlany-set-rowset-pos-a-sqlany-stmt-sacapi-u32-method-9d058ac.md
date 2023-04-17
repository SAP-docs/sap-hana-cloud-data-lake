<!-- loio9d058acba7d31014a029b23109b20f14 -->

# sqlany\_set\_rowset\_pos\(a\_sqlany\_stmt \*, sacapi\_u32\) Method

Sets the current row in the fetched row set.



```
public sacapi_bool sqlany_set_rowset_pos (
    a_sqlany_stmt * sqlany_stmt,
    sacapi_u32 row_num
)
```



## Parameters

sqlany\_stmt
:   A statement prepared successfully using sqlany\_prepare\(\).

row\_num
:   The row number within the row set. The valid values are from 0 to sqlany\_fetched\_rows\(\) - 1.



## Returns

1 on success or 0 on failure.



## Remarks

When a sqlany\_fetch\_absolute\(\) or sqlany\_fetch\_next\(\) function is executed, a row set is created and the current row is set to be the first row in the row set. The functions sqlany\_get\_column\(\), sqlany\_get\_data\(\), sqlany\_get\_data\_info\(\) are used to retrieve data at the current row.

**Related Information**  


[sqlany\_set\_rowset\_size\(a\_sqlany\_stmt \*, sacapi\_u32\) Method](sqlany-set-rowset-size-a-sqlany-stmt-sacapi-u32-method-9d0617f.md "Sets the size of the row set to be fetched by the sqlany_fetch_absolute() and sqlany_fetch_next() functions.")

[sqlany\_get\_column\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_data\_value \*\) Method](sqlany-get-column-a-sqlany-stmt-sacapi-u32-a-sqlany-data-value-method-3bf61bb.md "Fills the supplied buffer with the value fetched for the specified column at the current row.")

[sqlany\_get\_data\(a\_sqlany\_stmt \*, sacapi\_u32, size\_t, void \*, size\_t\) Method](sqlany-get-data-a-sqlany-stmt-sacapi-u32-size-t-void-size-t-method-3bf636f.md "Retrieves the data fetched for the specified column at the current row into the supplied buffer memory.")

[sqlany\_get\_data\_info\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_data\_info \*\) Method](sqlany-get-data-info-a-sqlany-stmt-sacapi-u32-a-sqlany-data-info-method-3bf62e4.md "Retrieves information about the fetched data at the current row.")

[sqlany\_fetch\_absolute\(a\_sqlany\_stmt \*, sacapi\_i32\) Method](sqlany-fetch-absolute-a-sqlany-stmt-sacapi-i32-method-3bf5955.md "Moves the current row in the result set to the specified row number and then fetches rows of data starting from the current row.")

[sqlany\_fetch\_next\(a\_sqlany\_stmt \*\) Method](sqlany-fetch-next-a-sqlany-stmt-method-3bf59e2.md "Returns the next set of rows from the result set.")

