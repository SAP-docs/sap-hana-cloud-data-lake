<!-- loio3bf98f9c6c5f10149a2fa819268d7734 -->

# SQLAnywhereInterface Structure

The SQL Anywhere C API interface structure.



```
typedef struct SQLAnywhereInterface
```



## Members

All members of SQLAnywhereInterface, including inherited members.

 **Variables** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Variable



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

dll\_handle



</td>
<td valign="top">

DLL handle.



</td>
</tr>
<tr>
<td valign="top">

public int



</td>
<td valign="top">

initialized



</td>
<td valign="top">

Flag to know if initialized or not.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_init



</td>
<td valign="top">

Pointer to sqlany\_init\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_fini



</td>
<td valign="top">

Pointer to sqlany\_fini\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_new\_connection



</td>
<td valign="top">

Pointer to sqlany\_new\_connection\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_free\_connection



</td>
<td valign="top">

Pointer to sqlany\_free\_connection\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_make\_connection



</td>
<td valign="top">

Pointer to sqlany\_make\_connection\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_connect



</td>
<td valign="top">

Pointer to sqlany\_connect\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_disconnect



</td>
<td valign="top">

Pointer to sqlany\_disconnect\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_execute\_immediate



</td>
<td valign="top">

Pointer to sqlany\_execute\_immediate\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_prepare



</td>
<td valign="top">

Pointer to sqlany\_prepare\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_free\_stmt



</td>
<td valign="top">

Pointer to sqlany\_free\_stmt\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_num\_params



</td>
<td valign="top">

Pointer to sqlany\_num\_params\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_describe\_bind\_param



</td>
<td valign="top">

Pointer to sqlany\_describe\_bind\_param\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_bind\_param



</td>
<td valign="top">

Pointer to sqlany\_bind\_param\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_send\_param\_data



</td>
<td valign="top">

Pointer to sqlany\_send\_param\_data\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_reset



</td>
<td valign="top">

Pointer to sqlany\_reset\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_get\_bind\_param\_info



</td>
<td valign="top">

Pointer to sqlany\_get\_bind\_param\_info\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_execute



</td>
<td valign="top">

Pointer to sqlany\_execute\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_execute\_direct



</td>
<td valign="top">

Pointer to sqlany\_execute\_direct\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_fetch\_absolute



</td>
<td valign="top">

Pointer to sqlany\_fetch\_absolute\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_fetch\_next



</td>
<td valign="top">

Pointer to sqlany\_fetch\_next\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_get\_next\_result



</td>
<td valign="top">

Pointer to sqlany\_get\_next\_result\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_affected\_rows



</td>
<td valign="top">

Pointer to sqlany\_affected\_rows\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_num\_cols



</td>
<td valign="top">

Pointer to sqlany\_num\_cols\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_num\_rows



</td>
<td valign="top">

Pointer to sqlany\_num\_rows\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_get\_column



</td>
<td valign="top">

Pointer to sqlany\_get\_column\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_get\_data



</td>
<td valign="top">

Pointer to sqlany\_get\_data\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_get\_data\_info



</td>
<td valign="top">

Pointer to sqlany\_get\_data\_info\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_get\_column\_info



</td>
<td valign="top">

Pointer to sqlany\_get\_column\_info\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_commit



</td>
<td valign="top">

Pointer to sqlany\_commit\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_rollback



</td>
<td valign="top">

Pointer to sqlany\_rollback\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_client\_version



</td>
<td valign="top">

Pointer to sqlany\_client\_version\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_error



</td>
<td valign="top">

Pointer to sqlany\_error\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_sqlstate



</td>
<td valign="top">

Pointer to sqlany\_sqlstate\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_clear\_error



</td>
<td valign="top">

Pointer to sqlany\_clear\_error\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_init\_ex



</td>
<td valign="top">

Pointer to sqlany\_init\_ex\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_fini\_ex



</td>
<td valign="top">

Pointer to sqlany\_fini\_ex\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_new\_connection\_ex



</td>
<td valign="top">

Pointer to sqlany\_new\_connection\_ex\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_make\_connection\_ex



</td>
<td valign="top">

Pointer to sqlany\_make\_connection\_ex\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_client\_version\_ex



</td>
<td valign="top">

Pointer to sqlany\_client\_version\_ex\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_cancel



</td>
<td valign="top">

Pointer to sqlany\_cancel\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_register\_callback



</td>
<td valign="top">

Pointer to sqlany\_register\_callback\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_set\_batch\_size



</td>
<td valign="top">

Pointer to sqlany\_set\_batch\_size\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_set\_param\_bind\_type



</td>
<td valign="top">

Pointer to sqlany\_set\_param\_bind\_type\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_get\_batch\_size



</td>
<td valign="top">

Pointer to sqlany\_get\_batch\_size\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_set\_rowset\_size



</td>
<td valign="top">

Pointer to sqlany\_set\_rowset\_size\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_get\_rowset\_size



</td>
<td valign="top">

Pointer to sqlany\_get\_rowset\_size\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_set\_column\_bind\_type



</td>
<td valign="top">

Pointer to sqlany\_set\_column\_bind\_type\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_bind\_column



</td>
<td valign="top">

Pointer to sqlany\_bind\_column\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_clear\_column\_bindings



</td>
<td valign="top">

Pointer to sqlany\_clear\_column\_bindings\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_fetched\_rows



</td>
<td valign="top">

Pointer to sqlany\_fetched\_rows\(\) function.



</td>
</tr>
<tr>
<td valign="top">

public void \*



</td>
<td valign="top">

sqlany\_set\_rowset\_pos



</td>
<td valign="top">

Pointer to sqlany\_set\_rowset\_pos\(\) function.



</td>
</tr>
</table>

**Related Information**  


[sqlany\_initialize\_interface\(SQLAnywhereInterface \*, const char \*\) Method](sqlany-initialize-interface-sqlanywhereinterface-const-char-method-3bf6e17.md "Initializes the SQLAnywhereInterface object and loads the DLL dynamically.")

