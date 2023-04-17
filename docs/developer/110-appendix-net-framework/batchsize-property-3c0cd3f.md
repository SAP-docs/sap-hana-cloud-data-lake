<!-- loio3c0cd3f06c5f10149894823f370fd404 -->

# BatchSize Property

Gets or sets the number of rows in each batch.



Visual Basic
:   ```
Public Property BatchSize As Integer
```

C\#
:   ```
public int BatchSize {get;set;}
```



## Remarks

At the end of each batch, the rows in the batch are sent to the database server.

The number of rows in each batch. The default is 0.

Setting this property to zero causes all the rows to be sent in one batch.

Setting this property to a value less than zero is an error.

If this value is changed while a batch is in progress, then the current batch completes and any further batches use the new value.

