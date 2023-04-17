<!-- loioe186e606a64b4aee95b98a6ee63e4531 -->

# Node.js Application Programming

Use the Node.js API to connect to data lake Relational Engine, issue SQL queries, and obtain result sets.

The driver supports Node.js 8.x and higher.



<a name="loioe186e606a64b4aee95b98a6ee63e4531__section_r44_wjj_qgb"/>

## Working with Node.js

The examples in this section show how to perform common tasks with the Node.js driver.

> ### Note:  
> The connection properties `host` and `port` are interchangeable with the `serverNode` connection property.

 Getting Started
 :   A database connection object is created by calling createConnection. The connection to data lake Relational Engine is established by calling the connection object's connection method and passing an object or string representing connection parameters, for example:

    ```
    var iq = require('@sap/iq-client');
    
    var conn = iq.createConnection();
    
    var connOptions = {host:'XXX-XXX.iq.hdl.us10.hanacloud.ondemand.com:443',uid:'XXXXXXX',pwd:'XXXXXXX',ENC:'TLS{tls_type=rsa;direct=yes}'};
    
    conn.connect(connOptions, function(err) {
      if (err) throw err;
      conn.exec('SELECT Name, Description FROM Products WHERE ID = ?', [301],
                function (err, result) {
        if (err) throw err;
    
        console.log('Name: ', result[0].Name, ', Description: ',
                    result[0].Description);
        // output --> Name: Tee Shirt, Description: V-neck
        conn.disconnect();
      })
    });
    ```

  Connecting
 :   A database connection object is created by specifying createConnection. The connection is established by calling the connection object's connect method and passing in an object or string representing connection parameters.

    The following example shows a TCP/IP connection to data lake Relational Engine:

    ```
    conn.connect({
      host: 'myserver',
      port: '443',
      uid: 'DBA',
      pwd: 'sql'
      ENC: 'TLS{tls_type=rsa;direct=yes}'
    });
    ```

  Disconnecting
 :   Disconnect from the database:

    ```
    conn.disconnect(function(err) {
      if (err) throw err;
      console.log('Disconnected');
    });
    ```

 

<a name="loioe186e606a64b4aee95b98a6ee63e4531__section_n3v_sfz_xrb"/>

## Direct Statement Execution

Direct statement execution is the simplest way to execute SQL statements. The input consists of the SQL command to be executed and an optional array of positional arguments. The result is returned by using callbacks. The type of returned result depends on the kind of statement.

 DDL Statement
 :   In the case of a successful DDL statement, nothing is returned.

    ```
    conn.exec('CREATE TABLE Test (ID INTEGER PRIMARY KEY, msg VARCHAR(128))',
      function (err, result) {
      if (err) throw err;
      console.log('Table Test created!');
    });
    ```

  DML Statement
 :   In the case of a DML statement the number of 'affectedRows' is returned.

    ```
    conn.exec("INSERT INTO Test VALUES(1, 'Hello')", function (err, affectedRows) {
      if (err) throw err;
      console.log('Number of affected rows:', affectedRows);
    });
    '''
    ```

  Query
 :   The exec function is a convenient way to completely retrieve the result of a query. In the below example all selected rows are fetched and returned in the callback:

    ```
    conn.exec("SELECT * FROM Test WHERE ID < 5", function (err, rows) {
      if (err) throw err;
      console.log('Rows:', rows);
    });
    ```

    Values in the query can be substitued with JavaScript variables by using '?' placeholders in the query and passing an array of positional arguments.

    ```
    conn.exec("SELECT * FROM Test WHERE ID BETWEEN ? AND ?", [5, 8],
      function (err, rows) {
      if (err) throw err;
      console.log('Rows:', rows);
    });
    ```

 

<a name="loioe186e606a64b4aee95b98a6ee63e4531__section_i5p_hgz_xrb"/>

## Prepared Statement Execution

Prepared statements can be used for performance gain if the same statement is going to be executed many times. The following describes how to execute prepared statements and queries with the Node.js driver.

 Prepare a Statement
 :   The connection returns a statement object that can be executed multiple times.

    ```
    conn.prepare('SELECT * FROM Test WHERE ID = ?', function (err, stmt){
      if (err) throw err;
    });
    ```

  Execute a Statement
 :   The execution of a prepared statement is similar to the direct statement execution. The first parameter of the exec function is an array with positional parameters.

    ```
    stmt.exec([16], function(err, rows) {
      if (err) throw err;
      console.log("Rows: ", rows);
    });
    ```

  Execute a Batch Statement
 :   The execution of a prepared batch statement is similar to the direct statement execution. The first parameter of the execBatch function is an array with positional parameters.

    ```
    var stmt=conn.prepare("INSERT INTO Customers(ID, NAME) VALUES(?, ?)");
    stmt.execBatch([[1, 'Company 1'], [2, 'Company 2']], function(err, rows) {
      if (err) throw err;
      console.log("Rows: ", rows);
    });
    ```

  Execute a Query
 :   The execution of a prepared query is similar to direct statement execution. The first parameter of the execQuery function is an array with positional parameters.

    ```
    var stmt=conn.prepare("SELECT * FROM Customers WHERE ID >= ? AND ID < ?");
    stmt.execQuery([100, 200], function(err, rs) {
      if (err) throw err;
        var rows = [];
        while (rs.next()) {
    	rows.push(rs.getValues());
        }
      console.log("Rows: ", rows);
    });
    ```

  Drop a Statement
 :   The below example drops a statement:

    ```
    stmt.drop(function(err) {
      if (err) throw err;
    });
    ```

 

<a name="loioe186e606a64b4aee95b98a6ee63e4531__section_dv2_5gz_xrb"/>

## Transaction Handling

Transactions are automatically committed.

 Commit a Transaction
 :   Setting auto commit to false implicitly starts a new transaction that must be explicitly committed.

    ```
    conn.setAutoCommit(false);
    
    conn.commit(function(err) {
      if (err) throw err;
      console.log('Transaction commited.');
    });
    ```

  Roll back a transaction
 :   Setting auto commit to false implicitly starts a new transaction that must be explicitly rolled back.

    ```
    conn.setAutoCommit(false);
    
    conn.rollback(function(err) {
      if (err) throw err;
      console.log('Transaction rolled back.');
    });
    ```

 **Related Information**  


[SAP HANA Data Management Suite](https://go.sap.com/community/topic/hana.html)

