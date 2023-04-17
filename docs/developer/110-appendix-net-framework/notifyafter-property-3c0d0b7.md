<!-- loio3c0d0b706c5f10148ce0d6f3d641e7d8 -->

# NotifyAfter Property

Gets or sets the number of rows to be processed before generating a notification event.



Visual Basic
:   ```
Public Property NotifyAfter As Integer
```

C\#
:   ```
public int NotifyAfter {get;set;}
```



## Remarks

Zero is returned if the property has not been set.

Changes made to NotifyAfter, while executing WriteToServer, do not take effect until after the next notification.

Setting this property to a value less than zero is an error.

The values of NotifyAfter and BulkCopyTimeout are mutually exclusive, so the event can fire even if no rows have been sent to the database or committed.

**Related Information**  


[BulkCopyTimeout Property](bulkcopytimeout-property-3c0cdbd.md "Gets or sets the number of seconds for the operation to complete before it times out.")

