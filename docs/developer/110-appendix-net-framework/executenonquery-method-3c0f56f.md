<!-- loio3c0f56fc6c5f10148caeaa340b728d68 -->

# ExecuteNonQuery\(\) Method

Executes a statement that does not return a result set, such as an INSERT, UPDATE, DELETE, or data definition statement.



Visual Basic
:   ```
Public Overrides Function ExecuteNonQuery () As Integer
```

C\#
:   ```
public override unsafe int ExecuteNonQuery ()
```



## Returns

The number of rows affected.



## Remarks

Use ExecuteNonQuery to change the data in a database without using a DataSet. Do this by executing UPDATE, INSERT, or DELETE statements.

Although ExecuteNonQuery does not return any rows, output parameters or return values that are mapped to parameters are populated with data.

For UPDATE, INSERT, and DELETE statements, the return value is the number of rows affected by the command. For all other types of statements, and for rollbacks, the return value is -1.

**Related Information**  


[ExecuteReader\(\) Method](executereader-method-3c0f5ee.md "Executes a SQL statement that returns a result set.")

