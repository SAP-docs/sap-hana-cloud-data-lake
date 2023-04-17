<!-- loio3bd571026c5f1014886e9a458d50bc13 -->

# Cursor Usage

When you execute a query in an application, the result set consists of several rows. In general, you do not know how many rows the application is going to receive before you execute the query.

Cursors provide a way of handling query result sets in applications. The way you use cursors and the kinds of cursors available to you depend on the programming interface you use.

Several system procedures are provided to help determine what cursors are in use for a connection, and what they contain:

-   sa\_list\_cursors system procedure
-   sa\_describe\_cursor system procedure
-   sa\_copy\_cursor\_to\_temp\_table system procedure

With cursors, you can perform the following tasks within any programming interface:

-   Loop over the results of a query.

-   Perform inserts, updates, and deletes on the underlying data at any point within a result set.


In addition, some programming interfaces allow you to use special features to tune the way result sets return to your application, providing substantial performance benefits for your application.

