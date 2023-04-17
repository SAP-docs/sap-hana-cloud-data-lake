<!-- loio81701ea56ce21014a58cbd85d49dfac9 -->

# SQL Variables in Data Lake Relational Engine

The supported variables can be grouped by scope: connection, database, and global.

When a variable is created, the initial value is set to NULL unless a default is specified. The value can later be changed by using the SET statement, the UPDATE statement, or a SELECT statement with an INTO clause.

Variables are not affected by COMMIT or ROLLBACK statements.

 Connection-scope variables
 :   Connection-scope variables are set and used in the context of a connection. They are not available to other connections. There are two types of connection-scope variables: **connection-level** and **local** \(also referred to as **declared**\). You can also create connection-scope variables of type TABLE REF to hold references to tables; these are called table reference variables.

     Connection-level variables
     :   Connection-level variables are created by using the CREATE VARIABLE statement and are typically used to make values available to any procedure executed by the connection.

        Connection-level variables persist only for the duration of the connection or until the variable is explicitly dropped by using the DROP VARIABLE statement.

      Local \(declared\) variables
     :   Local variables are created by using the DECLARE statement inside of a BEGIN...END block, and are typically used to store and modify values within the same compound statement that the local variable is declared in. Local variable values are not available for use outside of the context of the BEGIN...END block.

        Local variables persist only for the duration of the BEGIN...END block in which they are declared, and they can also be dropped.

   Database-scope variables
 :   Database-scope variables are used in the context of the database \(instead of connection\), and are a great way to share values across connections. Their intended use is to store small, infrequently changing, shared values. Storing large or frequently changing values may affect the performance of your application, and is not recommended. The initial values of database-scope variables persist after the database restarts \(that is, changes to their initial value do not persist between database restarts\). Database-scope variables can be used in the same manner as connection-scope and global variables, but they cannot be defined with the data type ROW, ARRAY, or TABLE REF.

     Database-scope variables owned by users
     :   When a database-scope variable is owned by a user, only that user can select from, and update, that variable, and can do so regardless of the connection.

        Database-scope variables can also be owned by a role. However, the only access to a database-scope variable owned by a role is through the stored procedures, user-defined functions, and events owned by that role.

      Database-scope variables owned by PUBLIC
     :   Database variables owned by PUBLIC are available to all users and connections provided the users have the right system privileges.

     Access to, and administration of, database-scope variables requires system privileges that vary depending on who owns the variable \(self, another user, or PUBLIC\). The following table summarizes the privileges required to access and administer database-scope variables:

    **Privileges required for administering database-scope variables**


    <table>
    <tr>
    <th valign="top">

    Action


    
    </th>
    <th valign="top">

    Owned by


    
    </th>
    <th valign="top">

    Privilege Required


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    Create a database-scope variable


    
    </td>
    <td valign="top">

    self


    
    </td>
    <td valign="top">

    MANAGE ANY DATABASE VARIABLE


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Create a database-scope variable


    
    </td>
    <td valign="top">

    another user


    
    </td>
    <td valign="top">

    MANAGE ANY DATABASE VARIABLE


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Create a database-scope variable


    
    </td>
    <td valign="top">

    PUBLIC


    
    </td>
    <td valign="top">

    MANAGE ANY DATABASE VARIABLE


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Update a database-scope variable


    
    </td>
    <td valign="top">

    self


    
    </td>
    <td valign="top">

    none required


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Update a database-scope variable


    
    </td>
    <td valign="top">

    another user


    
    </td>
    <td valign="top">

    not allowed


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Update a database-scope variable


    
    </td>
    <td valign="top">

    PUBLIC


    
    </td>
    <td valign="top">

    UPDATE PUBLIC DATABASE VARIABLE


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Select from a database-scope variable


    
    </td>
    <td valign="top">

    self


    
    </td>
    <td valign="top">

    none


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Select from a database-scope variable


    
    </td>
    <td valign="top">

    another user


    
    </td>
    <td valign="top">

    not allowed


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Select from a database-scope variable


    
    </td>
    <td valign="top">

    PUBLIC


    
    </td>
    <td valign="top">

    SELECT PUBLIC DATABASE VARIABLE


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Drop a database-scope variable


    
    </td>
    <td valign="top">

    self


    
    </td>
    <td valign="top">

    none required


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Drop a database-scope variable


    
    </td>
    <td valign="top">

    another user


    
    </td>
    <td valign="top">

    MANAGE ANY DATABASE VARIABLE


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Drop a database-scope variable


    
    </td>
    <td valign="top">

    PUBLIC


    
    </td>
    <td valign="top">

    MANAGE ANY DATABASE VARIABLE


    
    </td>
    </tr>
    </table>
    
  Global Variables
 :   Global variables are used in the context of the database, but can only be set by the database server. Although you cannot directly set a global variable, some global variable values are indirectly set in response to user activity. For example, some global variables, such as @@identity, hold connection-specific information, while other variables, such as @@connections, have values that are common to all connections.

    Global variables are visually distinguished from other variables by having two @ signs preceding their names. For example, @@error and @@rowcount are global variables.

 

## Variables and Aliases with Identical Names

It is possible to have a statement that has aliases and variables with identical names. This is the sequence the database server follows when processing an identifier to help you know how the reference is resolved:

1.  Match any aliases specified in the query SELECT list.

2.  Match column names for any referenced tables.

3.  Assume that the name is a variable.




## Standards

 ANSI/ISO SQL Standard
 :   Variables declared within SQL stored procedures or functions by using the DECLARE statement is supported in the ANSI/ISO SQL Standard as SQL Language Feature P002, "Computational completeness". CREATE VARIABLE, DROP VARIABLE, and global variables are not in the ANSI/ISO SQL Standard.

 