<!-- loio3be1a0396c5f1014ba3aed696627b972 -->

# How to Obtain Result Sets Using Python

Once you have obtained a handle to an open connection, you can access and modify data stored in the database. Perhaps the simplest operation is to retrieve some rows and print them out.

The *cursor* method is used to create a cursor on the open connection. The *execute* method is used to create a result set. The *fetchall* method is used to obtain the rows in this result set.

```
import sqlanydb
myuid = raw_input("Enter your user ID: ")
mypwd = raw_input("Enter your password: ")
# Create a connection object, then use it to create a cursor
con = sqlanydb.connect( userid=myuid, password=mypwd )
cursor = con.cursor()

# Execute a SQL string
sql = "SELECT * FROM Employees"
cursor.execute(sql)

# Get a cursor description which contains column names
desc = cursor.description
print(len(desc))

# Fetch all results from the cursor into a sequence, 
# display the values as column name=value pairs,
# and then close the connection
rowset = cursor.fetchall()
for row in rowset:
    for col in range(len(desc)):
        print("%s=%s" % (desc[col][0], row[col] ))
    print()
cursor.close()
con.close()
```

