<!-- loio3c1849da6c5f10149fc19627859b7d23 -->

# GetDataSources\(\) Method

Retrieves a DataTable containing information about all visible database servers.



Visual Basic
:   ```
Public Overrides Function GetDataSources () As DataTable
```

C\#
:   ```
public unsafe override DataTable GetDataSources ()
```



## Remarks

The returned table has four columns: ServerName, IPAddress, PortNumber, and DataBaseNames. There is a row in the table for each available database server.



The following code fills a DataTable with information for each database server that is available.

```
DataTable servers = SADataSourceEnumerator.Instance.GetDataSources();
```

