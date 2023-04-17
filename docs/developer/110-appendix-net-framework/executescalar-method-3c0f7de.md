<!-- loio3c0f7de06c5f1014b0e5cf92da135c96 -->

# ExecuteScalar\(\) Method

Executes a statement that returns a single value.



Visual Basic
:   ```
Public Overrides Function ExecuteScalar () As Object
```

C\#
:   ```
public override object ExecuteScalar ()
```



## Returns

The first column of the first row in the result set, or a null reference if the result set is empty.



## Remarks

If this method is called on a query that returns multiple rows and columns, then only the first column of the first row is returned.

