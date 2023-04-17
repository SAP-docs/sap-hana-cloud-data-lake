<!-- loio3c1600c86c5f1014b144c9ffd7b6de15 -->

# Close\(\) Method

Closes the SADataReader.



Visual Basic
:   ```
Public Overrides Sub Close ()
```

C\#
:   ```
public override void Close ()
```



## Remarks

Explicitly call the Close method when you are finished using the SADataReader.

When running in autocommit mode, a COMMIT is issued as a side effect of closing the SADataReader.

