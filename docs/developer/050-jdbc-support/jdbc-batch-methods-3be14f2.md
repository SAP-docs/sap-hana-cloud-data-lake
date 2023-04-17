<!-- loio3be14f286c5f1014838ac11005f69415 -->

# JDBC Batch Methods

The addBatch method of the PreparedStatement class is used for performing batched \(or wide\) inserts, deletes, updates, and merges. The following are some guidelines to using this method.

1.  A SQL statement should be prepared using one of the prepareStatement methods of the Connection class.

    ```
    String sqlStr = "INSERT INTO Departments( DepartmentID, DepartmentName ) VALUES ( ? , ? )";
    PreparedStatement pstmt = con.prepareStatement( sqlStr );
    ```

2.  The parameters for the prepared statement should be set and then added as a batch. The following outline creates n batches with m parameters in each batch:

    ```
    for( i=0; i < n; i++ ) 
    {
        pstmt.set...( 1, param_1 );
        pstmt.set...( 2, param_2 );
        .
        .
        .
        pstmt.set...( m , param_m );
        pstmt.addBatch(); 
    }
    ```

    The following example creates 5 batches with 2 parameters in each batch. The first parameter in an integer and the second parameter is a string.:

    ```
    for( i=0; i < 5; i++ ) 
    {    
        pstmt.setInt( 1, idValue[i] );
        pstmt.setString( 2, name[i] );
        pstmt.addBatch();
    }
    ```

3.  The batch must be executed using the executeBatch method of the PreparedStatement class.

    ```
    int[] affected = pstmt.executeBatch();
    ```


BLOB parameters are not supported in batches.

When using the data lake Relational Engine JDBC driver to perform batched inserts, use a small column size. Using batched inserts to insert large binary or character data into long binary or long varchar columns is not recommended and may degrade performance. The performance can decrease because the JDBC driver must allocate large amounts of memory to hold each of the batched insert rows.

In all other cases, batched inserts, deletes, updates, and merges should provide better performance than using individual operations.

