<!-- loio3bde67136c5f10149ed5f36711da63fc -->

# Benefits of Using Cursors

Although server-side cursors are not required in database applications, they do provide several benefits.

A server-side cursor is preferable to a client-side cursor for the following reasons:

Response time
:   Server-side cursors do not require that the whole result set be assembled before the first row is fetched by the client. A client-side cursor requires that the entire result set be obtained and transferred to the client before the first row is fetched by the client.

Client-side memory
:   For large result sets, obtaining the entire result set on the client side can lead to demanding memory requirements.

Concurrency control
:   If you make updates to your data and do not use server-side cursors in your application, you must send separate SQL statements like UPDATE, INSERT, or DELETE to the database server to apply changes. This raises the possibility of concurrency problems if any corresponding rows in the database have changed since the result set was delivered to the client. As a consequence, updates by other clients may be lost.

    Server-side cursors can act as pointers to the underlying data, permitting you to impose proper concurrency constraints on any changes made by the client by setting an appropriate isolation level.

