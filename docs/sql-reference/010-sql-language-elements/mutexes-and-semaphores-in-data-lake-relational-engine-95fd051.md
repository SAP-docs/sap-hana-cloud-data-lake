<!-- loio95fd05156ea11014ab3cefaf7344bda1 -->

# Mutexes and Semaphores in Data Lake Relational Engine

Use mutexes and semaphores in your application logic to achieve locking behavior and control and communicate the availability of resources.

Mutexes and semaphores are locking and signaling mechanisms that control the availability or use of a shared resource such as an external library or a procedure. You can include mutexes and semaphores to achieve the type of locking behavior your application requires. Choosing whether to use mutexes or semaphores depends on the requirements of your application.

Mutexes provide the application with a concurrency control mechanism; for example, they can be used to allow only one connection at a time to execute a critical section in a stored procedure, user-defined function, trigger, or event. Mutexes can also lock an application resource that does not directly correspond to a database object. Semaphores provide support for producer/consumer application logic in the database or for access to limited application resources.

Mutexes and semaphores benefit from the same deadlock detection as database row and table locks.

UPDATE ANY MUTEX SEMAPHORE allows locking/releasing of mutexes and notifying/waiting for semaphores, CREATE ANY MUTEX SEMAPHORE is necessary to create/replace, and DROP ANY MUTEX SEMAPHORE is necessary to drop/replace. To have a finer level of control on who can update a mutex or semaphore, you can grant privileges on the objects they are used in instead. For example, you can grant EXECUTE privilege on a system procedure that contains a mutex.



## More About Mutexes



A mutex is a lock and release mechanism that limits the availability of a critical section of a shared resource such as an external library or a stored procedure. Locking and unlocking a mutex is achieved by executing LOCK MUTEX and RELEASE MUTEX statements, respectively.

The **scope** of a mutex can be either *transaction* or *connection*. In transaction-scope mutexes, the lock is held until the end of the transaction that has locked the mutex. In connection-scope mutexes, the lock is held until a RELEASE MUTEX statement is executed by the connection or until the connection terminates.

The **mode** of a mutex can be either *exclusive* or *shared*. In exclusive mode, only the transaction or connection holding the lock can use the resource. In shared mode, multiple transactions or connections can lock the mutex.

You can recursively lock a mutex \(that is, you can nest LOCK MUTEX statements for the same mutex inside your code\). However, with connection-scope mutexes, an equal number of RELEASE MUTEX statements are required to release the mutex.

If a connection locks a mutex in shared mode, and then \(recursively\) locks it again in exclusive mode, then the lock remains held in exclusive mode until it is released twice, or until the end of the transaction.

Here is a simple scenario showing how you can use a mutex to protect a critical section of a stored procedure. In this scenario, the critical section can only be executed by one connection at a time \(but can span multiple transactions\):

1.  The following statement creates a new mutex to protect the critical section:

    ```
    CREATE MUTEX protect_my_cr_section SCOPE CONNECTION;
    ```

2.  The following statement locks the critical section in exclusive mode so that no other connection can access it:

    ```
    LOCK MUTEX protect_my_cr_section IN EXCLUSIVE MODE;
    ```

3.  The following statement releases the critical section:

    ```
    RELEASE MUTEX protect_my_cr_section;
    ```

4.  The following statement removes the mutex when the critical section no longer needs protection:

    ```
    DROP MUTEX protect_my_cr_section;
    ```




## More About Semaphores

A semaphore is a signaling mechanism that uses a counter to communicate the availability of a resource. Incrementing and decrementing the semaphore counter is achieved by executing NOTIFY SEMAPHORE and WAITFOR SEMAPHORE statements, respectively. Use semaphores in a resource availability model or in a producer-consumer model. Regardless of model, a semaphore cannot go below 0. That way, the counter is used to limit the availability of the resource \(a license, in this example\).

The **resource availability model** is when a counter is used to limit the availability of a resource. For example, suppose you have a license that restricts application use to 10 users at a time. You set the semaphore counter to 10 at create time using the START WITH clause. When a user logs in, a WAITFOR SEMAPHORE statement is executed, and the count is decremented by one. If the count is 0, then the user waits for up to the specified timeout period. If the counter goes above 0 before the timeout, then they log in. If not, then the user's login attempt times out. When the user logs out, a NOTIFY SEMAPHORE statement is executed, incrementing the count by one. Each time a user logs in, the count is decremented; each time they log out, the count is incremented.

The **producer-consumer model** is when a counter is used to signal the availability of a resource. For example, a procedure that consumes what another procedure produces. The consumer executes a WAITFOR SEMAPHORE statement and waits for something to process. When the producer has created output, it executes a NOTIFY SEMAPHORE statement to signal that work is available. This statement increments the counter associated with the semaphore. When the waiting consumer gets the work, the counter is decremented. In the producer-consumer model, the counter cannot go below 0, but it can go as high as the producers increment the counter.

Here is a simple scenario showing how you can use a semaphore to control the number of licenses for an application. The scenario assumes that there is a total of three licenses available, and that each successful log in to the application consumes one license:

1.  The following statement creates a new semaphore with the number of licenses specified as the initial count:

    ```
    CREATE SEMAPHORE license_counter START WITH 3;
    ```

2.  The following statement obtains a license using the license\_counter semaphore:

    ```
    WAITFOR SEMAPHORE license_counter;
    ```

3.  The following statement releases the license:

    ```
    NOTIFY SEMAPHORE license_counter INCREMENT BY 1;
    ```

4.  The following statement removes the semaphore when the application no longer needs to be limited by the license:

    ```
    DROP SEMAPHORE license_counter;
    ```


So, a common way to use semaphores in a producer-consumer model might look something like this:

```
CREATE SEMAPHORE producer_counter;
CREATE SEMAPHORE consumer_counter START WITH 100;

CREATE PROCEDURE DBA.MyProducer( )
   BEGIN
      WHILE 1 = 1 LOOP
          WAITFOR SEMAPHORE consumer_counter;
          -- produce some data and put it somewhere (e.g. a table)
          NOTIFY SEMAPHORE producer_counter;
      END LOOP
   END
go

CREATE PROCEDURE DBA.MyConsumer( )
   BEGIN
      WHILE 1 = 1 LOOP
          WAITFOR SEMAPHORE producer_counter;
          -- read the next bit of data and do something with it
          NOTIFY SEMAPHORE consumer_counter;
      END LOOP
   END
go

```

In this example, MyProducer and MyConsumer run in different connections. MyProducer fetches data and can get at most 100 iterations ahead of MyConsumer. If MyConsumer goes faster than MyProducer, producer\_counter eventually reaches 0. At that point, MyConsumer blocks until MyProducer makes more data. If MyProducer goes faster than MyConsumer, consumer\_counter eventually reaches 0. At that point, MyProducer blocks until MyConsumer consumes some data.

