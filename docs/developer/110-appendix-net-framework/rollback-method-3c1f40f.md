<!-- loio3c1f40f06c5f1014bd1ecddcc05dd628 -->

# Rollback\(\) Method

Rolls back a transaction from a pending state.



Visual Basic
:   ```
Public Overrides Sub Rollback ()
```

C\#
:   ```
public override void Rollback ()
```



## Remarks

The transaction can only be rolled back from a pending state \(after BeginTransaction has been called, but before Commit is called\).

