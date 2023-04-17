<!-- loio3be158146c5f1014995ce4ee9702c9e2 -->

# Setting up the Server-side JDBC Example

Compile and install a sample Java application into the database.



## Prerequisites

A Java Development Kit \(JDK\) must be installed.

To install a class, you must have the MANAGE ANY EXTERNAL OBJECT system privilege.



## Context

The source code for the JDBC example is located in <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\JDBC\JDBCExample.java</code>.



## Procedure

1.  At a command prompt, compile the `JDBCExample.java` source code.

    ```
    javac JDBCExample.java
    ```

2.  Connect to the database from Interactive SQL.

3.  Install the `JDBCExample.class` file into the sample database by executing the following statement in Interactive SQL:

    ```
    INSTALL JAVA NEW
    FROM FILE 'JDBCExample.class';
    ```

    If the database server was not started from the same directory as the class file and the path to the class file is not listed in the database server's class path, then you will have to include the path to the class file in the INSTALL statement. The database server's class path is defined by the -cp database server option and the java\_class\_path database option.


