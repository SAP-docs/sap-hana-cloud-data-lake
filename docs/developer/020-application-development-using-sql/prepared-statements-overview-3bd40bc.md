<!-- loio3bd40bc26c5f1014a2c5d100ae5b773e -->

# Prepared Statements Overview

The general procedure for using prepared statements is consistent, but the details vary from interface to interface.

Comparing how to use prepared statements in different interfaces illustrates this point.

You typically perform the following tasks to use a prepared statement:

1.  Prepare the statement.

2.  Bind the parameters that will hold values in the statement.

3.  Assign values to the bound parameters in the statement.

4.  Execute the statement.

5.  Repeat steps 3 and 4 as needed.

6.  Drop the statement when finished. In JDBC, the Java garbage collection mechanism drops the statement.




## Use a Prepared Statement in ODBC

You typically perform the following tasks to use a prepared statement in ODBC:

1.  Prepare the statement using SQLPrepare.

2.  Bind the statement parameters using SQLBindParameter.

3.  Execute the statement using SQLExecute.

4.  Drop the statement using SQLFreeStmt.


For more information about ODBC prepared statements, see the ODBC SDK documentation.



## Use a Prepared Statement in JDBC

You typically perform the following tasks to use a prepared statement in JDBC:

1.  Prepare the statement using the prepareStatement method of the connection object. This returns a prepared statement object.

2.  Set the statement parameters using the appropriate *set**<Type\>* methods of the prepared statement object. Here, *<Type\>* is the data type assigned.

3.  Execute the statement using the appropriate method of the prepared statement object. For inserts, updates, and deletes this is the executeUpdate method.




## Use a Prepared Statement in Embedded SQL

You typically perform the following tasks to use a prepared statement in Embedded SQL:

1.  Prepare the statement using the EXEC SQL PREPARE statement.

2.  Assign values to the parameters in the statement.

3.  Execute the statement using the EXEC SQL EXECUTE statement.

4.  Free the resources associated with the statement using the EXEC SQL DROP statement.




## Use a Prepared Statement in Open Client

You typically perform the following tasks to use a prepared statement in Open Client:

1.  Prepare the statement using the ct\_dynamic function, with a CS\_PREPARE type parameter.

2.  Set statement parameters using ct\_param.

3.  Execute the statement using ct\_dynamic with a CS\_EXECUTE type parameter.

4.  Free the resources associated with the statement using ct\_dynamic with a CS\_DEALLOC type parameter.


