<!-- loio3c15e8566c5f10148272b880be950859 -->

# UpdateBatchSize Property

Gets or sets the number of rows that are processed in each round-trip to the database server.



Visual Basic
:   ```
Public Overrides Property UpdateBatchSize As Integer
```

C\#
:   ```
public override int UpdateBatchSize {get;set;}
```



## Remarks

The default value is 1.

Setting the value to something greater than 1 causes SADataAdapter.Update to execute all the insert statements in batches. The deletions and updates are executed sequentially as before, but insertions are executed afterward in batches of size equal to the value of UpdateBatchSize. Setting the value to 0 causes Update to send the insert statements in a single batch.

Setting the value to something greater than 1 causes SADataAdapter.Fill to execute all the insert statements in batches. The deletions and updates are executed sequentially as before, but insertions are executed afterward in batches of size equal to the value of UpdateBatchSize.

Setting the value to 0 causes Fill to send the insert statements in a single batch.

Setting it less than 0 is an error.

If UpdateBatchSize is set to something other than one, and the InsertCommand property is set to something that is not an INSERT statement, then an exception is thrown when calling Fill.

This behavior is different from SqlDataAdapter. It batches all types of commands.

