<!-- loio58bc2932dd2a45db807824fd6eedede1 -->

# Model First to a New Database

If you plan to try Microsoft's Model First tutorial, then there are some steps that you must do differently.



## Prerequisites

You must have Microsoft Visual Studio and the .NET Framework installed on your computer.

You must have the CREATE ANY OBJECT system privilege.



## Context

Microsoft's Model First tutorial is designed for use with Microsoft's .NET data provider. The steps below provide guidance for using the data lake Relational Engine .NET Data Provider instead. Review these steps before attempting the tutorial.



## Procedure

1.  For Entity Framework 6, make sure that the data lake Relational Engine .NET Data Provider that supports this version is installed. Make sure there are no running instances of Microsoft Visual Studio. At a command prompt with administrator privileges, do the following:

    ```
    cd %SQLANY17%\Assembly\v4.5
    SetupVSPackage.exe /i /v EF6
    ```

2.  Before creating your Microsoft Visual Studio project, connect to the sample database using Interactive SQL and run the following SQL script to remove the Blogs, Posts, and Users tables, if you have already created them in another tutorial.

    ```
    DROP TABLE IF EXISTS [GROUPO].[Blogs];
    DROP TABLE IF EXISTS [GROUPO].[Posts];
    DROP TABLE IF EXISTS [GROUPO].[Users];
    ```

3.  Start Microsoft Visual Studio.

4.  In the Microsoft Visual Studio *Server Explorer*, use the *.NET Framework Data Provider for *SAP IQ* *17** to create a data connection. For *ODBC data source*, use SAP IQ 17 Demo. Fill in the *UserID* and *Password* fields. The *Test Connection* button is used to ensure that a connection can be made to the database.

5.  Immediately after creating your new project, install the latest version of Entity Framework 6 into the project, using the NuGet Package Manager.

    This step creates an `App.config` file that is not suitable for use with data lake Relational Engine.

6.  Replace the contents of `App.config` with the following.

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <configSections>
        <!-- For more information on Entity Framework configuration, visit http://go.microsoft.com/fwlink/?LinkID=237468 -->
        <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
      </configSections>
      <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
      </startup>
      <system.data>
          <DbProviderFactories>
              <clear />
              <add name="SAP IQ 17 Data Provider" invariant="Sap.Data.SQLAnywhere" description=".Net Framework Data Provider for SAP IQ 17" type="Sap.Data.SQLAnywhere.SAFactory, Sap.Data.SQLAnywhere.EF6, Version=17.0.0.10094, Culture=neutral, PublicKeyToken=f222fc4333e0d400" />
          </DbProviderFactories>
      </system.data>
      <entityFramework>
        <defaultConnectionFactory type="Sap.Data.SQLAnywhere.SAConnectionFactory, Sap.Data.SQLAnywhere.EF6, Version=17.0.0.10094, Culture=neutral, PublicKeyToken=f222fc4333e0d400">
            <parameters>
                <parameter value="DSN=SAP IQ 17 Demo;PWD=sql" />
            </parameters>
        </defaultConnectionFactory>
        <providers>
            <provider invariantName="Sap.Data.SQLAnywhere" type="Sap.Data.SQLAnywhere.SAProviderServices, Sap.Data.SQLAnywhere.EF6, Version=17.0.0.10094, Culture=neutral, PublicKeyToken=f222fc4333e0d400" />
        </providers>
      </entityFramework>
    </configuration>
    ```

7.  Update all occurrences of the data provider version number in `App.config`. The version number should match the version of the data provider that you have currently installed.

8.  Once you have updated `App.config`, you must build your project. This must be done before using the Entity Framework Designer.

9.  Before the Generating the Database step, open the *Properties* of `BloggingModel.edmx [Diagram1]` \(this is your design form\) and set *Database Schema Name* to GROUPO and set *DDL Generation Template* to `SSDLToSA17.tt (VS)`.

10. In the *Generate Database Wizard*, select the option to include sensitive data in the connection string.

11. Continue with the instructions in the remaining steps of the tutorial.




## Results

You have built an Entity Framework application that uses the Model First approach when the tables do not already exist in the database.

