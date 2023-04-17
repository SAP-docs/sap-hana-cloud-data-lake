<!-- loio3be1dc366c5f1014be45b8084f53e35a -->

# How to Return Result Sets from Java

Write a Java method that returns one or more result sets to the calling environment, and wrap this method in a SQL stored procedure.

The following code fragment illustrates how multiple result sets can be returned to the caller of this Java procedure. It uses three executeQuery statements to obtain three different result sets.

```
public static void Results( ResultSet[] rset )
       throws SQLException
{
    // Demonstrate returning multiple result sets

    Connection con = DriverManager.getConnection(
                    "jdbc:default:connection" );
    rset[0] = con.createStatement().executeQuery(
        "SELECT * FROM Employees" +
        "   ORDER BY EmployeeID" );
    rset[1] = con.createStatement().executeQuery(
        "SELECT * FROM Departments" +
        "   ORDER BY DepartmentID" );
    rset[2] = con.createStatement().executeQuery(
        "SELECT i.ID,i.LineID,i.ProductID,i.Quantity," +
        "       s.OrderDate,i.ShipDate," +
        "       s.Region,e.GivenName||' '||e.Surname" +
        "   FROM SalesOrderItems AS i" +
        "   JOIN SalesOrders AS s" +
        "   JOIN Employees AS e" +
        "   WHERE s.ID=i.ID" +
        "        AND s.SalesRepresentative=e.EmployeeID" );
    con.close();
}
```



## Notes

-   This server-side JDBC example is part of the `JDBCExample.java` file included in the <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\JDBC</code> directory.

-   It obtains a connection to the default running database by using getConnection.

-   The executeQuery methods return result sets.


