<!-- loio3be13cfb6c5f10148ddba4385f67c530 -->

# Prepared Statements

Each time a statement is sent to a database, the database server must perform a series of steps.

-   It must parse the statement and transform it into an internal form. This process is sometimes called **preparing** the statement.

-   It must verify the correctness of all references to database objects by checking, for example, that columns named in a query actually exist.

-   If the statement involves joins or subqueries, then the query optimizer generates an access plan.

-   It executes the statement after all these steps have been carried out.




## Reusing Prepared Statements Can Improve Performance

If you use the same statement repeatedly, for example inserting many rows into a table, repeatedly preparing the statement causes a significant and unnecessary overhead. To remove this overhead, some database programming interfaces provide ways of using prepared statements. A **prepared statement** is a statement containing a series of placeholders. When you want to execute the statement, assign values to the placeholders, rather than prepare the entire statement over again.

Using prepared statements is useful when carrying out many similar actions, such as inserting many rows.

Generally, using prepared statements requires the following steps:

Prepare the statement
:   In this step, you generally provide the statement with some placeholder character instead of the values.

Repeatedly execute the prepared statement
:   In this step, you supply values to be used each time the statement is executed. The statement does not have to be prepared each time.

Drop the statement
:   In this step, you free the resources associated with the prepared statement. Some programming interfaces handle this step automatically.



## Do Not Prepare Statements That Are Used Only Once

In general, do not prepare statements if they are only executed once. There is a slight performance penalty for separate preparation and execution, and it introduces unnecessary complexity into your application.

In some interfaces, however, you must prepare a statement to associate it with a cursor.

The calls for preparing and executing statements are not a part of SQL, and they differ from interface to interface. Each of the application programming interfaces provides a method for using prepared statements.

