<!-- loio3c1741de6c5f1014a23587183fdf178b -->

# Read\(\) Method

Reads the next row of the result set and moves the SADataReader to that row.



Visual Basic
:   ```
Public Overrides Function Read () As Boolean
```

C\#
:   ```
public override unsafe bool Read ()
```



## Returns

True if there are more rows; false otherwise.



## Remarks

The default position of the SADataReader is prior to the first record. Call Read to begin accessing any data.



The following code fills a listbox with the values in a single column of results.

```
while( reader.Read() ) {
   listResults.Items.Add( reader.GetValue( 0 ).ToString() );
}
listResults.EndUpdate();
reader.Close();
```

