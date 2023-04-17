<!-- loio3c1eb9ff6c5f10149613928ba3bf1034 -->

# SATcpOptionsBuilder\(string\) Constructor

Initializes an SATcpOptionsBuilder object.



Visual Basic
:   ```
Public Sub SATcpOptionsBuilder (ByVal options As String)
```

C\#
:   ```
public SATcpOptionsBuilder (string options)
```



## Parameters

options
:   A database server TCP connection parameter options string. For a list of connection parameters, see "Connection parameters".



The following statement initializes an SATcpOptionsBuilder object.

```
SATcpOptionsBuilder options = new SATcpOptionsBuilder("localonly=yes;port=6873");
```

