<!-- loio3bdeb76e6c5f10149541bf0202e74d6b -->

# Isolation Level Settings

You can set the isolation level of a current connection using the isolation\_level database option.

Some interfaces, such as ODBC, allow you to set the isolation level for a connection at connection time. You can reset this level later using the isolation\_level database option.

You can override any temporary or public settings for the isolation\_level database option within individual INSERT, UPDATE, DELETE, SELECT, UNION, EXCEPT, and INTERSECT statements by including an OPTION clause in the statement.

