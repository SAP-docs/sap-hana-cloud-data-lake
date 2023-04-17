<!-- loiobea2317ac2104e84979b446958cea96f -->

# Code First to a New Database

If you plan to try Microsoft's Code First to a New Database tutorial, then there are some steps that you must do differently.



## Prerequisites

You must have Microsoft Visual Studio and the .NET Framework installed on your computer.

You must have the CREATE ANY OBJECT system privilege.



## Context

Microsoft's Code First to a New Database tutorial is designed for use with Microsoft's .NET data provider. The steps below provide guidance for using the data lake Relational Engine .NET Data Provider instead. Review these steps before attempting the tutorial.



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

3.  Start Microsoft Visual Studio. The steps that follow were performed successfully using Microsoft Visual Studio 2013 and Entity Framework 6.1.3.

4.  One of the steps requires that you install the latest version of Entity Framework 6 into the project, using the NuGet Package Manager.

    This step creates an `App.config` file that is not suitable for use with data lake Relational Engine.

5.  Replace the contents of `App.config` with the following.

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

6.  Update all occurrences of the data provider version number in `App.config`. The version number should match the version of the data provider that you have currently installed.

7.  Once you have updated `App.config`, you must build your project.

8.  Continue with the instructions in the remaining steps of the tutorial. When you add the code for the BloggingContext class, you must revise it as follows to ensure that the owner of the tables is GROUPO \(otherwise, dbo is used\).

    ```
    public class BloggingContext : DbContext
    {
        public DbSet<Blog> Blogs { get; set; }
        public DbSet<Post> Posts { get; set; }
        protected override void OnModelCreating(DbModelBuilder modelBuilder)
        {
            modelBuilder.HasDefaultSchema("GROUPO");
        }
    }
    ```




## Results

You have built an Entity Framework application that uses the Code First approach when the tables do not already exist in the database.

