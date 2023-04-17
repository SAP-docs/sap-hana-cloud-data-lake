<!-- loio3bd3ed246c5f101486e29ae5fc493e0f -->

# Host Variables in Embedded SQL

Host variables are C variables that are identified to the Embedded SQL preprocessor. Host variables can be used to send values to the database server or receive values from the database server.

Host variables are quite easy to use, but they have some restrictions. Dynamic SQL is a more general way of passing information to and from the database server using a structure known as the SQL Descriptor Area \(SQLDA\). The Embedded SQL preprocessor automatically generates a SQLDA for each statement in which host variables are used.

Host variables cannot be used in batches. Host variables cannot be used within a subquery in a SET statement.

