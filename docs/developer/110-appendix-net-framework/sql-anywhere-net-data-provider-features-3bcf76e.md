<!-- loio3bcf76e26c5f1014a105d4e1f851e912 -->

# SQL Anywhere .NET Data Provider Features

The Microsoft .NET Framework is supported through three distinct namespaces.

 Sap.Data.SQLAnywhere
 :   The ADO.NET object model is an all-purpose data access model. ADO.NET components were designed to factor data access from data manipulation. There are two central components of ADO.NET that do this: the DataSet, and the .NET Framework data provider, which is a set of components including the Connection, Command, DataReader, and DataAdapter objects. A .NET Entity Framework Data Provider is included that communicates directly with a database server without adding the overhead of OLE DB or ODBC. The .NET Data Provider is represented in the .NET namespace as Sap.Data.SQLAnywhere.

    The SQL Anywhere .NET Data Provider namespace is described in this document.

  System.Data.Oledb
 :   This namespace supports OLE DB data sources. This namespace is an intrinsic part of the Microsoft .NET Framework. You can use System.Data.Oledb together with the OLE DB provider, SAOLEDB, to access databases.

  System.Data.Odbc
 :   This namespace supports ODBC data sources. This namespace is an intrinsic part of the Microsoft .NET Framework. You can use System.Data.Odbc together with the ODBC drivers to access databases.

 There are some key benefits to using the .NET Data Provider:

-   In the .NET environment, the .NET Data Provider provides native access to a database. Unlike the other supported providers, it communicates directly with a database server and does not require bridge technology.

-   As a result, the .NET Data Provider is faster than the OLE DB and ODBC Data Providers. It is the recommended Data Provider for accessing data lake Relational Engine databases.


