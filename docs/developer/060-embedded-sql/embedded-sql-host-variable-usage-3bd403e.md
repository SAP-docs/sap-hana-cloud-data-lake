<!-- loio3bd403ed6c5f10149c3dc1b3fad2335a -->

# Embedded SQL Host Variable Usage

Host variables can be used in a variety of circumstances.

Host variables can be used with the following:

-   SELECT, INSERT, UPDATE, and DELETE statements in any place where a number or string constant is allowed.

-   The INTO clause of SELECT and FETCH statements.

-   Host variables can also be used in place of a statement name, a cursor name, or an option name in statements specific to Embedded SQL.

-   For CONNECT, DISCONNECT, and SET CONNECT statements, a host variable can be used in place of a server name, database name, connection name, user ID, password, or connection string.

-   For SET OPTION and GET OPTION, a host variable can be used in place of the option value.


Host variables cannot be used in the following circumstances:

-   Host variables cannot be used in place of a table name or a column name in any statement.

-   Host variables cannot be used in batches.

-   Host variables cannot be used within a subquery in a SET statement.




## SQLCODE and SQLSTATE host variables

The ISO/ANSI standard allows an Embedded SQL source file to declare the following special host variables within an Embedded SQL declaration section:

```
long SQLCODE;
char SQLSTATE[6];
```

If used, these variables are set after any Embedded SQL statement that makes a database request \(EXEC SQL statements other than DECLARE SECTION, INCLUDE, WHENEVER SQLCODE, and so on\). As a consequence, the SQLCODE and SQLSTATE host variables must be visible in the scope of every Embedded SQL statement that generates database requests.

The following is valid Embedded SQL:

```
EXEC SQL INCLUDE SQLCA;
// declare SQLCODE with global scope
EXEC SQL BEGIN DECLARE SECTION;
long SQLCODE;
EXEC SQL END DECLARE SECTION;
sub1() {
 EXEC SQL BEGIN DECLARE SECTION;
 char SQLSTATE[6];
 EXEC SQL END DECLARE SECTION;
 exec SQL CREATE TABLE ...
}
sub2() {
 EXEC SQL BEGIN DECLARE SECTION;
 char SQLSTATE[6];
 EXEC SQL END DECLARE SECTION;
 exec SQL DROP TABLE ...
}
```

The following is not valid Embedded SQL because SQLSTATE is not defined in the scope of the function sub2:

```
EXEC SQL INCLUDE SQLCA;
sub1() {
 EXEC SQL BEGIN DECLARE SECTION;
 char SQLSTATE[6];
 EXEC SQL END DECLARE SECTION;
 exec SQL CREATE TABLE...
}
sub2() {
 exec SQL DROP TABLE...
}
```

The Embedded SQL preprocessor -k option permits the declaration of the SQLCODE variable outside the scope of an Embedded SQL declaration section.

