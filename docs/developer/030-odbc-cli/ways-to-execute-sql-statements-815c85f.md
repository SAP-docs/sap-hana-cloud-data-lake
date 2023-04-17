<!-- loio815c85f06ce210148731da8fc602de38 -->

# Ways to Execute SQL Statements

ODBC includes several functions for executing SQL statements.

Direct execution
:   The database server parses the SQL statement, prepares an access plan, and executes the statement. Parsing and access plan preparation are called **preparing** the statement.

Prepared execution
:   The statement preparation is carried out separately from the execution. For statements that are to be executed repeatedly, this avoids repeated preparation and so improves performance.

