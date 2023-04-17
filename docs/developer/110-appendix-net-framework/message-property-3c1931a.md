<!-- loio3c1931a16c5f10148629f1919503091e -->

# Message Property

Returns the text describing the error.



Visual Basic
:   ```
Public ReadOnly Overrides Property Message As String
```

C\#
:   ```
public override string Message {get;}
```



## Remarks

This method returns a single string that contains a concatenation of all of the Message properties of all of the SAError objects in the Errors collection. Each message, except the last one, is followed by a carriage return.

**Related Information**  


[SAError Class](saerror-class-3c18a7f.md "Collects information relevant to a warning or error returned by the data source.")

