<!-- loio3c11853b6c5f1014b097edc6c19c3f82 -->

# ConnectionTimeout Property

Gets the number of seconds before a connection attempt times out with an error.



Visual Basic
:   ```
Public ReadOnly Overrides Property ConnectionTimeout As Integer
```

C\#
:   ```
public override int ConnectionTimeout {get;}
```



## Remarks

The default ConnectionTimeout value is 15 seconds.



The following statement displays the value of the ConnectionTimeout.

```
MessageBox.Show( conn.ConnectionTimeout.ToString( ) );
```

