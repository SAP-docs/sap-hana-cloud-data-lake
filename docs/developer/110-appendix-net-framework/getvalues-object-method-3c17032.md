<!-- loio3c17032a6c5f1014a02796361800595d -->

# GetValues\(object\[\]\) Method

Gets all the columns in the current row.



Visual Basic
:   ```
Public Overrides Function GetValues (ByVal values As Object()) As Integer
```

C\#
:   ```
public override unsafe int GetValues (object[] values)
```



## Parameters

values
:   An array of objects that holds an entire row of the result set.



## Returns

The number of objects in the array.



## Remarks

For most applications, the GetValues method provides an efficient means for retrieving all columns, rather than retrieving each column individually.

You can pass an Object array that contains fewer than the number of columns contained in the resulting row. Only the amount of data the Object array holds is copied to the array. You can also pass an Object array whose length is more than the number of columns contained in the resulting row.

This method returns DBNull for NULL database columns.

