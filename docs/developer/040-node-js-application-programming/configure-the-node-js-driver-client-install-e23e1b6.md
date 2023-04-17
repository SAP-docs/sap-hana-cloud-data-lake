<!-- loioe23e1b6efe0b41fa894848ae456f6969 -->

# Configure the Node.js Driver \(Client Install\)

Configure the Node.js driver so that you can use it to connect to data lake Relational Engine.



<a name="loioe23e1b6efe0b41fa894848ae456f6969__context_jyb_qm4_2gb"/>

## Context

The Node.js driver is included with the data lake client install.



## Procedure

Install the driver.


<table>
<tr>
<th valign="top">

Driver location



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

**Install the driver that is included with the client install**



</td>
<td valign="top">

1.  Run the following command:

    ```
    npm install @sap/iq-client
    ```

    > ### Note:  
    > Before installing the driver, npm must be initialized with a `npm init -y` command.

2.  Run the following command to use the @sap/iq-client module:

    ```
    require('@sap/iq-client')
    ```




</td>
</tr>
<tr>
<td valign="top">

**Deploy on Linux Alpine**



</td>
<td valign="top">

Install libstdc++ as an APK package first, then install it as a dependency:

```
apk add --update --no-cache libstdc++ 
```

If libstdc++ is not installed then the following error is returned:

```
Error loading shared library libstdc++.so.6: No such file or directory (needed by iq-client.node)  
```



</td>
</tr>
</table>



The following example shows how to create a connection to data lake Relational Engine and execute a query:

```
var iq = require('@sap/iq-client');

var conn = iq.createConnection();

var conn_params = {host:'XXX-XXX.iq.hdl.us10.hanacloud.ondemand.com:443',uid:'XXXXXXX',pwd:'XXXXXXX',ENC:'TLS{tls_type=rsa;direct=yes}'};

conn.connect(conn_params, function(err) {
  if (err) throw err;
  conn.exec('SELECT Name, Description FROM Products WHERE id = ?', [301], function (err, result) {
    if (err) throw err;

    console.log('Name: ', result[0].Name, ', Description: ', result[0].Description);
    // output --> Name: Tee Shirt, Description: V-neck
    conn.disconnect();
  })
});
```

