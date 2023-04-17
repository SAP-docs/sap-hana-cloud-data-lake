<!-- loio3bd0edc66c5f10149f3dc6f6aa844786 -->

# db\_cancel\_request Function

Cancel an active request.



```
int db_cancel_request( SQLCA * <sqlca> );
```



## Parameters

sqlca
:   A pointer to a SQLCA structure.



## Returns

1 when the cancel request is sent; 0 if no request is sent.



## Remarks

Cancels the currently active database server request. This function checks to make sure a database server request is active before sending the cancel request.

A non-zero return value does not mean that the request was canceled. There are a few critical timing cases where the cancel request and the response from the database or server cross. In these cases, the cancel simply has no effect, even though the function still returns TRUE.

The db\_cancel\_request function can be called asynchronously. This function and db\_is\_working are the only functions in the database interface library that can be called asynchronously using a SQLCA that might be in use by another request.

If you cancel a request that is carrying out a cursor operation, the position of the cursor is indeterminate. You must locate the cursor by its absolute position or close it, following the cancel.

