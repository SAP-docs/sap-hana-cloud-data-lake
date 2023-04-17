<!-- loio3c0d3db36c5f101485538cb397bba361 -->

# SARowsCopied Event

This event occurs every time the number of rows specified by the NotifyAfter property have been processed.



Visual Basic
:   ```
Public Event SARowsCopied  As SARowsCopiedEventHandler
```

C\#
:   ```
public SARowsCopiedEventHandler SARowsCopied;
```



## Remarks

The receipt of an SARowsCopied event does not imply that any rows have been sent to the database server or committed. You cannot call the Close method from this event.

**Related Information**  


[NotifyAfter Property](notifyafter-property-3c0d0b7.md "Gets or sets the number of rows to be processed before generating a notification event.")

