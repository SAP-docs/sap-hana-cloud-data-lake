<!-- loio3bd3d6256c5f1014968a8053d1ecb361 -->

# BLOB Handling in .NET Applications

When fetching long string values or binary data, there are methods that you can use to fetch the data in pieces. For binary data, use the GetBytes method, and for string data, use the GetChars method.



Otherwise, BLOB data is treated in the same manner as any other data you fetch from the database.



## C\# GetChars BLOB Example

The following example reads three columns from a result set. The first two columns are integers, while the third column is a LONG VARCHAR. The length of the third column is computed by reading this column with the GetChars method in chunks of 100 characters.

```
SAConnection conn = new SAConnection( 
    "Data Source=SAP IQ 17 Demo;Password="+pwd );
conn.Open();
SACommand cmd = new SACommand("SELECT * FROM MarketingInformation", conn);
SADataReader reader = cmd.ExecuteReader();

int idValue;
int productIdValue;
int length = 100;
char[] buf = new char[length];
while (reader.Read())
{
    idValue = reader.GetInt32(0);
    productIdValue = reader.GetInt32(1);
    long blobLength = 0;
    long charsRead;
    while ((charsRead = reader.GetChars(2, blobLength, buf, 0, length))
            == (long)length)
    {
        blobLength += charsRead;
    }
    blobLength += charsRead;
}
reader.Close();
conn.Close();
```

