<!-- loio08917a9b4292435180b5c4420a7d2564 -->

# clearPool\(\[Function\]\) Method

Empties the connection pool.



```
connection.clearPool([callback] )
```



<a name="loio08917a9b4292435180b5c4420a7d2564__section_dv1_hjq_4cb"/>

## Parameters


<table>
<tr>
<th valign="top">

Type



</th>
<th valign="top">

Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Function



</td>
<td valign="top">

`callback`



</td>
<td valign="top">

The optional callback function.



</td>
</tr>
</table>



<a name="loio08917a9b4292435180b5c4420a7d2564__section_iby_yjf_gcb"/>

## Returns

The number of connections in the pool.



<a name="loio08917a9b4292435180b5c4420a7d2564__section_f4m_k3q_4cb"/>

## Remarks

By default, the node.js driver does not have connection pooling enabled. Enable connection pooling by setting the `pooling` connection property to TRUE.

When you close a pooled connection, the node.js driver does the following things:

1.  It stores the connection in the connection pool.
2.  It also cleans up the connection by:
    -   Rolling back the transaction
    -   Unsetting all session variables
    -   Setting the isolation level \(the node.js driver sets isolation level to the default value \(read committed\) or the value provided by the user\)
    -   Resetting the locale when a pooled connection is returned to the connection pool if the user provided the locale with the connection string or connection properties
    -   Setting the schema if it is provided by the user

3.  It adds a new Connection.clearPool.
4.  It empties the connection pool.

The node.js driver does not drop temporary tables when a pooled connection is closed.



This method can be synchronous or asynchronous. Specify a callback function to use this method asynchronously. The callback function is of the form:

```js
function(err){
    };
```



The following synchronous example shows how to use the clearPool method.

```js
var conn = iq.createClient(connStr);
var count = conn.clearPool();
```

