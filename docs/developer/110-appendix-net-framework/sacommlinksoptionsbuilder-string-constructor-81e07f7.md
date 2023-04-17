<!-- loio81e07f796ce21014b30cc45fe86f0d38 -->

# SACommLinksOptionsBuilder\(string\) Constructor

Initializes an SACommLinksOptionsBuilder object.



Visual Basic
:   ```
Public Sub SACommLinksOptionsBuilder (ByVal options As String)
```

C\#
:   ```
public SACommLinksOptionsBuilder (string options)
```



## Parameters

options
:   A CommLinks connection parameter string. For a list of connection parameters, see "Connection parameters".



The following statement initializes an SACommLinksOptionsBuilder object.

```
SACommLinksOptionsBuilder commLinks =
 new SACommLinksOptionsBuilder("TCPIP(DoBroadcast=ALL;Timeout=20)");
```

