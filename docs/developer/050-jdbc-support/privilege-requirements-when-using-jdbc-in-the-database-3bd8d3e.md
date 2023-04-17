<!-- loio3bd8d3e66c5f10148841a4669412136e -->

# Privilege Requirements When Using JDBC in the Database

With the correct set of privileges, users can execute methods in Java classes.

Access privileges
:   Like all Java classes in the database, classes containing JDBC statements can be accessed by any user if the GRANT EXECUTE statement has granted them privilege to execute the stored procedure that is acting as a wrapper for the Java method.

Execution privileges
:   Java classes execute with the privileges of the stored procedure that is acting as a wrapper for the Java method \(by default, this is SQL SECURITY DEFINER\).

