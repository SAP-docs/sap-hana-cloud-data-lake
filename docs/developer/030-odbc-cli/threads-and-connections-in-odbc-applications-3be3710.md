<!-- loio3be371096c5f10148c5dba6c64c98453 -->

# Threads and Connections in ODBC Applications

You can develop multithreaded ODBC applications. Use a separate connection for each thread.

You can use a single connection for multiple threads. However, the database server does not allow more than one active request for any one connection at a time. If one thread executes a statement that takes a long time, all other threads must wait until the request is complete.

