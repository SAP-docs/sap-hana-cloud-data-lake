<!-- loio3bd3aed06c5f1014b1588c778b156f8d -->

# Entity Framework Support

The data lake Relational Engine .NET Data Provider supports Entity Framework 5.0 and 6.0, separate packages available from Microsoft.

To use Entity Framework 5.0 or 6.0, you must add it to Microsoft Visual Studio using Microsoft's NuGet Package Manager.

One of the new features of Entity Framework is Code First. It enables a different development workflow: defining data model objects by simply writing Microsoft Visual C\# .NET or Microsoft Visual Basic .NET classes mapping to database objects without ever having to open a designer or define an XML mapping file. Optionally, additional configuration can be performed by using data annotations or the Fluent API. Models can be used to generate a database schema or map to an existing database.

Here's an example which creates new database objects using the model:

```
using System;
using System.Collections.Generic;
using System.ComponentModel.DataAnnotations;
using System.Data.Entity;
using System.Data.Entity.Infrastructure;
using System.Linq;
using Sap.Data.SQLAnywhere;

namespace CodeFirstExample
{
    [Table( "EdmCategories", Schema = "DBA" )]
    public class Category
    {
        public string CategoryID { get; set; }
        [MaxLength( 64 )]
        public string Name { get; set; }

        public virtual ICollection<Product> Products { get; set; }
    }

    [Table( "EdmProducts", Schema = "DBA" )]
    public class Product
    {
        public int ProductId { get; set; }
        [MaxLength( 64 )]
        public string Name { get; set; }
        public string CategoryID { get; set; }

        public virtual Category Category { get; set; }
    }

    [Table( "EdmSuppliers", Schema = "DBA" )]
    public class Supplier
    {
        [Key]
        public string SupplierCode { get; set; }
        [MaxLength( 64 )]
        public string Name { get; set; }
    }

    public class Context : DbContext
    {
        public Context() : base() { }
        public Context( string connStr ) : base( connStr ) { }

        public DbSet<Category> Categories { get; set; }
        public DbSet<Product> Products { get; set; }
        public DbSet<Supplier> Suppliers { get; set; }

        protected override void OnModelCreating( DbModelBuilder modelBuilder )
        {
            modelBuilder.Entity<Supplier>().Property( s => s.Name ).IsRequired();
        }
    }
 
    class Program
    {
        static void Main( string[] args )
        {
            Database.DefaultConnectionFactory = new SAConnectionFactory();
            Database.SetInitializer<Context>( 
                new DropCreateDatabaseAlways<Context>() );

            using ( var db = new Context( 
                "DSN=SAP IQ 17 Demo;Password="+pwd ) )
            {
                var query = db.Products.ToList();
            }
        }
    }
}
```

To build and run this example, the following assembly references must be added:

```
EntityFramework
Sap.Data.SQLAnywhere.v4.5
System.ComponentModel.DataAnnotations
System.Data.Entity
```

Here is another example that maps to an existing database:

```
using System;
using System.Collections.Generic;
using System.ComponentModel.DataAnnotations;
using System.Data.Entity;
using System.Data.Entity.Infrastructure;
using System.Linq;
using Sap.Data.SQLAnywhere;

namespace CodeFirstExample
{
    [Table( "Customers", Schema = "GROUPO" )]
    public class Customer
    {
        [Key()]
        public int ID { get; set; }
        public string SurName { get; set; }
        public string GivenName { get; set; }
        public string Street { get; set; }
        public string City { get; set; }
        public string State { get; set; }
        public string Country { get; set; }
        public string PostalCode { get; set; }
        public string Phone { get; set; }
        public string CompanyName { get; set; }

        public virtual ICollection<Contact> Contacts { get; set; }
    }

    [Table( "Contacts", Schema = "GROUPO" )]
    public class Contact
    {
        [Key()]
        public int ID { get; set; }
        public string SurName { get; set; }
        public string GivenName { get; set; }
        public string Title { get; set; }
        public string Street { get; set; }
        public string City { get; set; }
        public string State { get; set; }
        public string Country { get; set; }
        public string PostalCode { get; set; }
        public string Phone { get; set; }
        public string Fax { get; set; }

        [ForeignKey( "Customer" )]
        public int CustomerID { get; set; }
        public virtual Customer Customer { get; set; }
    }

    public class Context : DbContext
    {
        public Context() : base() { }
        public Context( string connStr ) : base( connStr ) { }

        public DbSet<Contact> Contacts { get; set; }
        public DbSet<Customer> Customers { get; set; }
    }

    class Program
    {
        static void Main( string[] args )
        {
            Database.DefaultConnectionFactory = new SAConnectionFactory();
            Database.SetInitializer<Context>( null );

            using ( var db = new Context( 
                "DSN=SAP IQ 17 Demo;Password="+pwd ) )
            {
                foreach ( var customer in db.Customers.ToList() )
                {
                    Console.WriteLine( "Customer - " + string.Format( 
                      "{0}, {1}, {2}, {3}, {4}, {5}, {6}, {7}, {8}, {9}",
                        customer.ID, customer.SurName, customer.GivenName, 
                        customer.Street, customer.City, customer.State, 
                        customer.Country, customer.PostalCode, 
                        customer.Phone, customer.CompanyName ) );

                    foreach ( var contact in customer.Contacts )
                    {
                        Console.WriteLine( "    Contact - " + string.Format( 
                          "{0}, {1}, {2}, {3}, {4}, {5}, {6}, {7}, {8}, {9}, {10}",
                            contact.ID, contact.SurName, contact.GivenName, 
                            contact.Title, 
                            contact.Street, contact.City, contact.State, 
                            contact.Country, contact.PostalCode, 
                            contact.Phone, contact.Fax ) );
                    }
                }
            }
        }
    }
}
```

Be aware that there are some implementation detail differences between the Microsoft .NET Framework Data Provider for Microsoft SQL Server \(SqlClient\) and the .NET Data Provider.

1.  A new class SAConnectionFactory \(implements IDbConnectionFactory\) is included. You set the Database.DefaultConnectionFactory to an instance of SAConnectionFactory before creating any data model as shown below:

    ```
    Database.DefaultConnectionFactory = new SAConnectionFactory();
    ```

2.  The major principle of Entity Framework Code First is coding by conventions. The Entity Framework infers the data model by coding conventions. Entity Framework also does lots of things implicitly. Sometimes the developer might not realize all these Entity Framework conventions. But some code conventions do not make sense for database management systems like data lake Relational Engine. There are some differences between Microsoft SQL Server and these database servers.

    -   Microsoft SQL Server permits access to multiple databases with a single sign-on. Data lake Relational Engine permits a connection to one database at a time.

    -   If the user creates a user-defined DbContext using the parameterless constructor, SqlClient will connect to Microsoft SQL Server Express on the local computer using integrated security. The .NET Data Provider connects to the default server using integrated login if the user has already created a login mapping.

    -   SqlClient drops the existing database and creates a new database when the Entity Framework calls DbDeleteDatabase or DbCreateDatabase \(Microsoft SQL Server Express Edition only\). The .NET Data Provider never drops or creates the database. It creates or drops the database objects \(tables, relations, constraints for example\). The user must create the database first.

    -   The IDbConnectionFactory.CreateConnection method treats the string parameter "nameOrConnectionString" as database name \(initial catalog for Microsoft SQL Server\) or a connection string. If the user does not provide the connection string for DbContext, SqlClient automatically connects to the SQL Express server on the local computer using the namespace of user-defined DbContext class as the initial catalog. For *SQL Anywhere*, that parameter can only contain a connection string. A database name is ignored and integrated login is used instead.


3.  The Microsoft SQL Server SqlClient API maps a column with data annotation attribute TimeStamp to Microsoft SQL Server data type timestamp/rowversion. There are some misconceptions about Microsoft SQL Server timestamp/rowversion among developers. The Microsoft SQL Server timestamp/rowversion data type is different from *SQL Anywhere* and most other RDBMS:

    -   The Microsoft SQL Server timestamp/rowversion is binary\(8\). It is does not support a combined date and time value. Data lake Relational Engine supports a data type called timestamp that is equivalent to the Microsoft SQL Server datetime data type.

    -   Microsoft SQL Server timestamp/rowversion values are guaranteed to be unique. Data lake Relational Engine timestamp values are not unique.

    -   A Microsoft SQL Server timestamp/rowversion value changes every time the row is updated.


    The TimeStamp data annotation attribute is not supported by the .NET Data Provider.

4.  By default, Entity Framework 4.1 always sets the schema or owner name to dbo which is the default schema of Microsoft SQL Server. However, dbo is not appropriate for data lake Relational Engine databases. For data lake Relational Engine, you must specify the schema or owner name \(GROUPO for example\) with the table name either by using data annotations or the Fluent API. Here is an example:

    ```
    namespace CodeFirstTest
    {
        public class Customer
        {
            [Key()]
            public int ID { get; set; }
            public string SurName { get; set; }
            public string GivenName { get; set; }
            public string Street { get; set; }
            public string City { get; set; }
            public string State { get; set; }
            public string Country { get; set; }
            public string PostalCode { get; set; }
            public string Phone { get; set; }
            public string CompanyName { get; set; }
    
            public virtual ICollection<Contact> Contacts { get; set; }
        }
    
        public class Contact
        {
            [Key()]
            public int ID { get; set; }
            public string SurName { get; set; }
            public string GivenName { get; set; }
            public string Title { get; set; }
            public string Street { get; set; }
            public string City { get; set; }
            public string State { get; set; }
            public string Country { get; set; }
            public string PostalCode { get; set; }
            public string Phone { get; set; }
            public string Fax { get; set; }
    
            [ForeignKey( "Customer" )]
            public int CustomerID { get; set; }
            public virtual Customer Customer { get; set; }
        }
    
        [Table( "Departments", Schema = "GROUPO" )]
        public class Department
        {
            [Key()]
            public int DepartmentID { get; set; }
            public string DepartmentName { get; set; }
            public int DepartmentHeadID { get; set; }
        }
    
        public class Context : DbContext
        {
            public Context() : base() { }
            public Context( string connStr ) : base( connStr ) { }
    
            public DbSet<Contact> Contacts { get; set; }
            public DbSet<Customer> Customers { get; set; }
            public DbSet<Department> Departments { get; set; }
    
            protected override void OnModelCreating( DbModelBuilder modelBuilder )
            {
                modelBuilder.Entity<Contact>().ToTable( "Contacts", "GROUPO" );
                modelBuilder.Entity<Customer>().ToTable( "Customers", "GROUPO" );
            }
        }
    }
    ```


