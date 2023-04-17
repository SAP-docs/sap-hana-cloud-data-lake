<!-- loio37fb9e8558e94547b66156b9298be16f -->

# Database First to an Existing Database

If you plan to try Microsoft's Database First to an Existing Database tutorial, then there are some steps that you must do differently.



## Prerequisites

You must have Microsoft Visual Studio and the .NET Framework installed on your computer.

You must have the CREATE ANY OBJECT system privilege.



## Context

Microsoft's Database First to an Existing Database tutorial is designed for use with Microsoft's .NET data provider. The steps below provide guidance for using the data lake Relational Engine .NET Data Provider instead. Review these steps before attempting the tutorial.



## Procedure

1.  For Entity Framework 6, make sure that the data lake Relational Engine .NET Data Provider that supports this version is installed. Make sure there are no running instances of Microsoft Visual Studio. At a command prompt with administrator privileges, do the following:

    ```
    cd %SQLANY17%\Assembly\v4.5
    SetupVSPackage.exe /i /v EF6
    ```

2.  Before creating your Microsoft Visual Studio project, connect to the sample database using Interactive SQL and run the following SQL script to set up the Blogs, Posts, and Users tables. It is very similar to the one presented in Microsoft's tutorials but uses the GROUPO schema owner instead of *dbo*.

    ```
    CREATE TABLE [GROUPO].[Blogs] ( 
        [BlogId] INT DEFAULT AUTOINCREMENT NOT NULL, 
        [Name] NVARCHAR (200) NULL, 
        [Url]  NVARCHAR (200) NULL, 
        CONSTRAINT [PK_GROUPO.Blogs] PRIMARY KEY CLUSTERED ([BlogId] ASC) 
    ); 
     
    CREATE TABLE [GROUPO].[Posts] ( 
        [PostId] INT DEFAULT AUTOINCREMENT NOT NULL, 
        [Title] NVARCHAR (200) NULL, 
        [Content] NTEXT NULL, 
        [BlogId] INT NOT NULL, 
        CONSTRAINT [PK_GROUPO.Posts] PRIMARY KEY CLUSTERED ([PostId] ASC), 
        CONSTRAINT [FK_GROUPO.Posts_GROUPO.Blogs_BlogId] FOREIGN KEY ([BlogId]) 
            REFERENCES [GROUPO].[Blogs] ([BlogId]) ON DELETE CASCADE 
    );
    
    INSERT INTO [GROUPO].[Blogs] ([Name],[Url]) 
    VALUES ('SAP SQL Anywhere', 'http://scn.sap.com/community/sql-anywhere') 
     
    INSERT INTO [GROUPO].[Blogs] ([Name],[Url]) 
    VALUES ('SAP Business Trends', 'http://scn.sap.com/community/business-trends')
    
    CREATE TABLE [GROUPO].[Users] 
    ( 
        [Username] NVARCHAR(50) NOT NULL PRIMARY KEY,  
        [DisplayName] LONG NVARCHAR NULL 
    )
    ```

3.  Start Microsoft Visual Studio. The steps that follow were performed successfully using Microsoft Visual Studio 2013 and Entity Framework 6.1.3.

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
        </defaultConnectionFactory>
        <providers>
            <provider invariantName="Sap.Data.SQLAnywhere" type="Sap.Data.SQLAnywhere.SAProviderServices, Sap.Data.SQLAnywhere.EF6, Version=17.0.0.10094, Culture=neutral, PublicKeyToken=f222fc4333e0d400" />
        </providers>
      </entityFramework>
    </configuration>
    ```

7.  Update all occurrences of the data provider version number in `App.config`. The version number should match the version of the data provider that you have currently installed.

8.  Once you have updated `App.config`, you must build your project. This must be done before the Reverse Engineer Model step.

9.  In the *Entity Data Model Wizard*, select the option to include sensitive data in the connection string.

10. Rather than select all tables, expand GROUPO in *Tables* and select the Blogs and Posts tables.

11. Continue with the instructions in the remaining steps of the tutorial.




## Results

You have built an Entity Framework application that uses the Database First approach for tables that already exist in the database.

