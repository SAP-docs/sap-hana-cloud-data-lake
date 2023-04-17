<!-- loio3bd02ce86c5f101482b78476939fb83a -->

# Data Lake Relational Engine JDBC Driver

Learn the characteristics of the data lake Relational Engine JDBC driver.

-   This driver is the recommended JDBC driver for connecting to databases.

-   The driver performs automatic JDBC driver registration with the JAVA VM. It is therefore sufficient to have the sajdbc4.jar file in the class file path and simply call DriverManager.getConnection\(\) with a URL that begins with jdbc:sqlanywhere.

-   With this driver, metadata for NCHAR data now returns the column type as java.sql.Types.NCHAR, NVARCHAR, or LONGNVARCHAR. In addition, applications can now fetch NCHAR data using the Get/SetNString or Get/SetNClob methods instead of the Get/SetString and Get/SetClob methods.


