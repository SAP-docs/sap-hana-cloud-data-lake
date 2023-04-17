<!-- loio3bd351036c5f1014a65689175daa4226 -->

# Request Management with Embedded SQL

Since a typical Embedded SQL application must wait for the completion of each database request before carrying out the next step, an application that uses multiple execution threads can carry on with other tasks.

If you must use a single execution thread, then some degree of multitasking can be accomplished by registering a callback function using the db\_register\_a\_callback function with the DB\_CALLBACK\_WAIT option. Your callback function is called repeatedly by the interface library while the database server or client library is busy processing your database request.

In your callback function, you cannot start another database request but you can cancel the current request using the db\_cancel\_request function. You can use the db\_is\_working function in your message handlers to determine if you have a database request in progress.

