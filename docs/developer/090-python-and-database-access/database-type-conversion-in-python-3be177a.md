<!-- loio3be177a36c5f101489bacce622f0cc89 -->

# Database Type Conversion in Python

To control how database types are mapped into Python objects when results are fetched from the database server, conversion callbacks can be registered.

Callbacks are registered using the module level register\_converter method. This method is called with the database type as the first parameter and the conversion function as the second parameter. For example, to request that sqlanydb create Decimal objects for data in any column described as having type DT\_DECIMAL, you would use the following example:

```
import sqlanydb
import decimal

def convert_to_decimal(num):
    return decimal.Decimal(num)

sqlanydb.register_converter(sqlanydb.DT_DECIMAL, convert_to_decimal)
```

By default columns of type DT\_BIT are converted to an integer type. To request that sqlanydb create boolean objects for data in any column described as having type DT\_BIT, you would use the following example:

```
import sqlanydb

def convert_to_boolean(num):
    return num != 0

sqlanydb.register_converter(sqlanydb.DT_DECIMAL, convert_to_decimal)
```

Converters may be registered for the following database types:

```
DT_DATE
DT_TIME
DT_TIMESTAMP
DT_VARCHAR
DT_FIXCHAR
DT_LONGVARCHAR
DT_STRING
DT_DOUBLE
DT_FLOAT
DT_DECIMAL
DT_INT
DT_SMALLINT
DT_BINARY
DT_LONGBINARY
DT_TINYINT
DT_BIGINT
DT_UNSINT
DT_UNSSMALLINT
DT_UNSBIGINT
DT_BIT
```

The following example demonstrates how to convert decimal results to integer resulting in the truncation of any digits after the decimal point. The salary amount displayed when the application is run is an integral value.

```
import sqlanydb

def convert_to_int(num):
    return int(float(num)) 

sqlanydb.register_converter(sqlanydb.DT_DECIMAL, convert_to_int)

myuid = raw_input("Enter your user ID: ")
mypwd = raw_input("Enter your password: ")

# Create a connection object, then use it to create a cursor
con = sqlanydb.connect( userid=myuid, password=mypwd )

cursor = con.cursor()

# Execute a SQL string
sql = "SELECT * FROM Employees WHERE EmployeeID=105"
cursor.execute(sql)

# Get a cursor description which contains column metadata
desc = cursor.description
print ("Number of columns = %d\n" % len(desc))

# Fetch all results from the cursor into a sequence and
# display the column metadata and values as name:value pairs

rowset = cursor.fetchall()
for row in rowset:
    col = 0
    for column in cursor.description:
        name, type_code, display_size, internal_size, precision, scale, null_ok = column
        
        print ("Column name: %s" % name)
        print ("Type code: %s" % type_code)
        print ("Display size: %s" % display_size)
        print ("Internal size: %d" % internal_size)
        print ("Precision: %d" % precision)
        print ("Scale: %d" % scale)
        print ("Null OK: %d" % null_ok)
        print ("Value: %s" % row[col])
        if type_code == sqlanydb.BINARY:
            print ("Python type: BINARY")
        if type_code == sqlanydb.DATE:
            print ("Python type: DATE")
        if type_code == sqlanydb.DATETIME:
            print ("Python type: DATETIME")
        if type_code == sqlanydb.NUMBER:
            print ("Python type: NUMBER")
        if type_code == sqlanydb.STRING:
            print ("Python type: STRING")
        if type_code == sqlanydb.TIME:
            print ("Python type: TIME")
        if type_code == sqlanydb.TIMESTAMP:
            print ("Python type: TIMESTAMP")
        print ("")
        col = col + 1

cursor.close()
con.close()
```

