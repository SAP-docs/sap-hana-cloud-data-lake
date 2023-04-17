<!-- loio3be167b16c5f101492fbb83fca706758 -->

# Using the SQL Anywhere .NET Data Provider in a Microsoft Visual Studio Project

Use the SQL Anywhere .NET Data Provider to develop Microsoft .NET applications with Microsoft Visual Studio by including both a reference to the SQL Anywhere .NET Data Provider, and a line in your source code referencing the SQL Anywhere .NET Data Provider classes.



## Procedure

1.  Start Microsoft Visual Studio and create or open your project.

2.  In the *Solution Explorer* window, right-click *References* and click *Add Reference*.

    The reference indicates which provider to include and locates the code for the SQL Anywhere .NET Data Provider.

3.  Click the *.NET* tab \(or open *Assemblies/Extensions*\), and scroll through the list to locate any of the following:

    -   Sap.Data.SQLAnywhere for .NET 3.5
    -   Sap.Data.SQLAnywhere for .NET 4
    -   Sap.Data.SQLAnywhere for .NET 4.5
    -   Sap.Data.SQLAnywhere for Entity Framework 6

    The choices for provider may be governed by your project's Target framework.

4.  Click the desired provider, make sure the checkbox for the selected provider is checked if one is present, and then click *OK*.

    The provider is added to the *References* folder in the *Solution Explorer* window of your project.

5.  Specify a directive to your source code to assist with the use of the SQL Anywhere .NET Data Provider namespace and the defined types.

    Add the following line to your project:

    -   If you are using C\#, add the following line to the list of `using` directives at the beginning of your source code:

        ```
        using Sap.Data.SQLAnywhere;
        ```

    -   If you are using Visual Basic, add the following line at the beginning of source code:

        ```
        Imports Sap.Data.SQLAnywhere
        ```





## Results

The SQL Anywhere .NET Data Provider is set up for use with your SQL Anywhere .NET application.



The following C\# example shows how to create a connection object when a *using* directive has been specified:

```
SAConnection conn = new SAConnection();
```

The following C\# example shows how to create a connection object when a *using* directive has not been specified:

```
Sap.Data.SQLAnywhere.SAConnection conn = 
    new Sap.Data.SQLAnywhere.SAConnection();
```

The following Microsoft Visual Basic example shows how to create a connection object when an *Imports* directive has been specified:

```
Dim conn As New SAConnection()
```

The following Microsoft Visual Basic example shows how to create a connection object when an *Imports* directive has not been specified:

```
Dim conn As New Sap.Data.SQLAnywhere.SAConnection()
```

