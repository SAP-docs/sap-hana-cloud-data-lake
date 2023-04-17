<!-- loio5cd53282816b419b9e60ee11c7b6f20a -->

# getRowCount\(\) Method

Gets the number of rows in the current result set.



```
resultset.getRowCount()
```



## Returns

This function returns the number of rows in the current result set. In many cases, the client does not know the total number of rows. Returns -1 if unknown, 0 if there are no rows, or +*<n\>* with *<n\>* specifying the exact number of rows valued at greater than 0. +*<n\>* is only available after the app has fetched the last chunk of rows.

