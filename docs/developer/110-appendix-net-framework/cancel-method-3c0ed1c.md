<!-- loio3c0ed1c06c5f1014a3cafd043c1d3846 -->

# Cancel\(\) Method

Cancels the execution of an SACommand object.



Visual Basic
:   ```
Public Overrides Sub Cancel ()
```

C\#
:   ```
public override void Cancel ()
```



## Remarks

If there is nothing to cancel, then nothing happens. If there is a command in process, then a "Statement interrupted by user" exception is thrown.

