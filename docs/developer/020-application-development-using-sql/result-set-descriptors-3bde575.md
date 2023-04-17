<!-- loio3bde57516c5f10148132bcd128060941 -->

# Result Set Descriptors

Some applications build SQL statements that cannot be completely specified in the application. Sometimes statements are dependent on a user response before the application knows exactly what information to retrieve, such as when a reporting application allows a user to select which columns to display.

In such a case, the application needs a method for retrieving information about both the nature of the **result set** and the contents of the result set. The information about the nature of the result set, called a **descriptor**, identifies the data structure, including the number and type of columns expected to be returned. Once the application has determined the nature of the result set, retrieving the contents is straightforward.

This **result set metadata** \(information about the nature and content of the data\) is manipulated using descriptors. Obtaining and managing the result set metadata is called **describing**.

Since cursors generally produce result sets, descriptors and cursors are closely linked, although some interfaces hide the use of descriptors from the user. Typically, statements needing descriptors are either SELECT statements or stored procedures that return result sets.

A sequence for using a descriptor with a cursor-based operation is as follows:

1.  Allocate the descriptor. This may be done implicitly, although some interfaces allow explicit allocation as well.

2.  Prepare the statement.

3.  Describe the statement. If the statement is a stored procedure call or batch, and the result set is not described by a RESULT clause in the procedure definition, then the describe should occur after opening the cursor.

4.  Declare and open a cursor for the statement \(Embedded SQL\) or execute the statement.

5.  Get the descriptor and modify the allocated area if necessary. This is often done implicitly.

6.  Fetch and process the statement results.

7.  Deallocate the descriptor.

8.  Close the cursor.

9.  Drop the statement. Some interfaces do this automatically.




## Implementation Notes

-   In Embedded SQL, a SQLDA \(SQL Descriptor Area\) structure holds the descriptor information.

-   In ODBC, a descriptor handle allocated using SQLAllocHandle provides access to the fields of a descriptor. You can manipulate these fields using SQLSetDescRec, SQLSetDescField, SQLGetDescRec, and SQLGetDescField.

    Alternatively, you can use SQLDescribeCol, SQLColAttribute, or SQLColAttributes \(ODBC 2.0\) to obtain column information.

-   In Open Client, you can use ct\_dynamic to prepare a statement and ct\_describe to describe the result set of the statement. However, you can also use ct\_command to send a SQL statement without preparing it first and use ct\_results to handle the returned rows one by one. This is the more common way of operating in Open Client application development.

-   In JDBC, the java.sql.ResultSetMetaData class provides information about result sets.

-   You can also use descriptors for sending data to the database server \(for example, with the INSERT statement\); however, this is a different kind of descriptor than for result sets.


