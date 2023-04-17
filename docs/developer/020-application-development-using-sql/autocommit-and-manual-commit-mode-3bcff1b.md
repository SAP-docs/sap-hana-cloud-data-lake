<!-- loio3bcff1be6c5f10149a098f4ca036e6d7 -->

# Autocommit and Manual Commit Mode

Database programming interfaces can operate in either **manual commit** mode or **autocommit** mode.

Manual commit mode
:   Operations are committed only when your application carries out an explicit commit operation or when the database server carries out an automatic commit, for example when executing an ALTER TABLE statement or other data definition statement. Manual commit mode is also sometimes called **chained mode**.

    To use transactions in your application, including nested transactions and savepoints, you must operate in manual commit mode.

Autocommit mode
:   Each statement is treated as a separate transaction. Autocommit mode is equivalent to appending a COMMIT statement to the end of each of your SQL statements. Autocommit mode is also sometimes called **unchained mode**.

Autocommit mode can affect the performance and behavior of your application. Do not use autocommit if your application requires transactional integrity.

