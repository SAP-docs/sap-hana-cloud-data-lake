<!-- loio3bd38f6e6c5f10148fb4818608f880f4 -->

# How to Fetch Data Using Embedded SQL

Fetching data in Embedded SQL is done using the SELECT statement.

There are two cases:

The SELECT statement returns at most one row
:   Use an INTO clause to assign the returned values directly to host variables.

The SELECT statement may return multiple rows
:   Use cursors to manage the rows of the result set.

