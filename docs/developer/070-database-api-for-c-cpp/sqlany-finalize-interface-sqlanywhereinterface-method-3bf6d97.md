<!-- loio3bf6d9736c5f1014a093b1ad33832f28 -->

# sqlany\_finalize\_interface\(SQLAnywhereInterface \*\) Method

Unloads the C API DLL library and resets the SQLAnywhereInterface structure.



```
public void sqlany_finalize_interface (SQLAnywhereInterface * api)
```



## Parameters

api
:   An initialized structure to finalize.



## Remarks

Use the following statement to include the function prototype:

```
#include "sacapidll.h"
```

Use this method to finalize and free resources associated with the SQL Anywhere C API DLL.

Examples of how the sqlany\_finalize\_interface method is used can be found in the C API examples in the `sdk\dbcapi\examples` directory of your SQL Anywhere installation.

