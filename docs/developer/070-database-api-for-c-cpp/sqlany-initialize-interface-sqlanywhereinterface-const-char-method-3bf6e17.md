<!-- loio3bf6e17b6c5f1014861bf85d22c4c4e9 -->

# sqlany\_initialize\_interface\(SQLAnywhereInterface \*, const char \*\) Method

Initializes the SQLAnywhereInterface object and loads the DLL dynamically.



```
public int sqlany_initialize_interface (
    SQLAnywhereInterface * api,
    const char * optional_path_to_dll
)
```



## Parameters

api
:   An API structure to initialize.

optional\_path\_to\_dll
:   An optional argument that specifies a path to the SQL Anywhere C API DLL.



## Returns

1 on successful initialization, and 0 on failure.



## Remarks

Use the following statement to include the function prototype:

```
#include "sacapidll.h"
```

This function attempts to load the SQL Anywhere C API DLL dynamically and looks up all the entry points of the DLL. The fields in the SQLAnywhereInterface structure are populated to point to the corresponding functions in the DLL. If the optional path argument is NULL, the environment variable SQLANY\_DLL\_PATH is checked. If the variable is set, the library attempts to load the DLL specified by the environment variable. If that fails, the interface attempts to load the DLL directly \(this relies on the environment being setup correctly\).

Examples of how the sqlany\_initialize\_interface method is used can be found in the C API examples in the `sdk\dbcapi\examples` directory of your SQL Anywhere installation.

