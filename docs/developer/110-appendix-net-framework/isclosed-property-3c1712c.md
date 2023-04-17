<!-- loio3c1712c46c5f1014a03cde76a30dd438 -->

# IsClosed Property

Gets a values that indicates whether the SADataReader is closed.



Visual Basic
:   ```
Public ReadOnly Overrides Property IsClosed As Boolean
```

C\#
:   ```
public override bool IsClosed {get;}
```



## Remarks

True if the SADataReader is closed; false otherwise.

IsClosed and RecordsAffected are the only properties that you can use after the SADataReader is closed.

