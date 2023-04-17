<!-- loio3bcf6ec56c5f1014ab1385abb8cf77c8 -->

# Time Values

The .NET Framework does not have a Time structure. To fetch time values from a database, you must use the GetTimeSpan method.



This method returns the data as a .NET Framework TimeSpan object.



## C\# TimeSpan Example

The following example uses the GetTimeSpan method to return the time as TimeSpan.

```
SAConnection conn = new SAConnection( 
    "Data Source=SAP IQ 17 Demo;Password="+pwd );
conn.Open();
SACommand cmd = new SACommand("SELECT 123, CURRENT TIME", conn);
SADataReader reader = cmd.ExecuteReader();
while (reader.Read())
{
    int ID = reader.GetInt32(0);
    TimeSpan time = reader.GetTimeSpan(1);
}
reader.Close();
conn.Close();
```

