<!-- loio3bd5a89b6c5f1014ad1bae9e04645f43 -->

# JDBC Program Structure

JDBC applications typically connect to a database, execute one or more SQL statements, process result sets, and then disconnect from the database.

The following are elements of a typical JDBC application:

 Create a Connection object
 :   The getConnection method of the DriverManager class creates a Connection object, and establishes a connection with a database.

  Create a Statement object
 :   The createStatement method of the Connection object creates a Statement object.

  Execute a SQL statement
 :   The execute method of the Statement object executes a SQL statement within the database environment. If one or more result sets are available, the boolean result `true` is returned.

  Process one or more result sets
 :   The getResultSet and getMoreResults methods of the Statement object are used to obtain result sets.

    The ResultSet object is used to obtain the data returned from the SQL statement, one row at a time.

  Loop over the rows of each result set
 :   The next method of the ResultSet object is used to position to the next available row in the result set. When no more rows are available, the boolean result `false` is returned.

  For each row, retrieve the values
 :   Values are retrieved for each column in the ResultSet object by identifying either the name or position of the column. You can use the getString method to get the value from a column on the current row.

  Release JDBC objects at the appropriate time
 :   The close method of each JDBC object releases resources to the system.

 The following example demonstrates the principles outlined above.

```
import java.io.*;
import java.sql.*;

public class results
{
    public static void main(String[] args) throws Exception
    {
        Connection conn = null;
        try
        {
            conn = DriverManager.getConnection(
                    "jdbc:sqlanywhere:uid=HDLADMIN;pwd=XXXXXXXXX" );
            String SQL = "BEGIN\n"
                + " SELECT * FROM Departments "
                + "     ORDER BY DepartmentID;\n"
                + " SELECT EmployeeID, Surname, GivenName "
                + "     FROM Employees e "
                + "     JOIN Departments d "
                + "     ON DepartmentHeadID = EmployeeID "
                + "     ORDER BY d.DepartmentID\n"
                + "END";
            Statement stmt = conn.createStatement();
            if( stmt.execute(SQL) )
            {
                ResultSet rs = stmt.getResultSet();
                while( rs != null )
                {
                    System.out.println( "\n---Result set---\n" );
                    while (rs.next())
                    {
                        System.out.println(rs.getString(1)
                                + ", " + rs.getString(2)
                                + ", " + rs.getString(3) );
                    }
                    if( stmt.getMoreResults() )
                    {
                        rs = stmt.getResultSet();
                    }
                    else
                    {
                        rs.close();
                        rs = null;
                    }
                }
            }
            stmt.close();
        }
        catch (Exception e)
        {
            e.printStackTrace();
        }
        if( conn != null) conn.close();
    }
}
```

Java objects can use JDBC objects to interact with a database and get data for their own use.

