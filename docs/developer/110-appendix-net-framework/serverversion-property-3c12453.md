<!-- loio3c12453c6c5f1014a0b2b8ff3302a467 -->

# ServerVersion Property

Gets a string that contains the version of the instance of the database server to which the client is connected.



Visual Basic
:   ```
Public ReadOnly Overrides Property ServerVersion As String
```

C\#
:   ```
public override string ServerVersion {get;}
```



## Returns

The version of the instance of the database server.



## Remarks

The version is \#\#.\#\#.\#\#\#\#, where the first two digits are the major version, the next two digits are the minor version, and the last four digits are the release version. The appended string is of the form major.minor.build, where major and minor are two digits, and build is four digits.

