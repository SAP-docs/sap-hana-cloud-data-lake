<!-- loio95ebd85c6ea11014aa449ce4706bbebd -->

# sp\_list\_mutexes\_semaphores System Procedure for Data Lake Relational Engine

Returns information about all temporary and permanent mutexes and semaphores, including which connection is holding each mutex and whether a semaphore is being waited for.



```
sp_list_mutexes_semaphores( [<oid>] )
```



## Parameters


<dl>
<dt><b>

oid

</b></dt>
<dd>

\(For internal use only\) The unsigned bigint object ID parameter. Use the default parameter value NULL.



</dd>
</dl>



## Result Set


<table>
<tr>
<th valign="top">

Column name



</th>
<th valign="top">

Type



</th>
<th valign="top">

Column description



</th>
</tr>
<tr>
<td valign="top">

*<mutex\_semaphore\_id\>*



</td>
<td valign="top">

UNSIGNED INTEGER



</td>
<td valign="top">

The ID for the object. If the object is permanent, the ID value is the same as found SYSMUTEXSEMAPHORE system view. If the object is temporary, the value is the internally-generated temporary ID.



</td>
</tr>
<tr>
<td valign="top">

*<creator\>*



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

The owner of the mutex or semaphore



</td>
</tr>
<tr>
<td valign="top">

*<"name"\>*



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

The name of the mutex or semaphore



</td>
</tr>
<tr>
<td valign="top">

*<"type"\>*



</td>
<td valign="top">

VARCHAR\(9\)



</td>
<td valign="top">

The type of object. The value 'mutex:T' is for transaction-scope mutexes, the value 'mutex:C' is for connection-scope mutexes, and the value 'semaphore' is for semaphores.



</td>
</tr>
<tr>
<td valign="top">

*<is\_temp\>*



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

'Y' or 'N' indicating whether the mutex or semaphore is temporary.



</td>
</tr>
<tr>
<td valign="top">

*<is\_dropped\>*



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

'Y' or 'N' indicating whether the mutex or semaphore is dropped but not yet released. Y indicates that the mutex was dropped but still needs to be released, N indicates the mutex was dropped and released. This value is always N for semaphores



</td>
</tr>
<tr>
<td valign="top">

*<start\_with\>*



</td>
<td valign="top">

UNSIGNED INTEGER



</td>
<td valign="top">

The initial value of the semaphore. This value is always NULL for mutexes.



</td>
</tr>
<tr>
<td valign="top">

*<current\_count\>*



</td>
<td valign="top">

UNSIGNED INTEGER



</td>
<td valign="top">

The current value of the semaphore. This value is always NULL for mutexes.



</td>
</tr>
<tr>
<td valign="top">

*<currently\_owned\_by\>*



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

A comma-separated list of connection IDs for connections currently holding the mutex locked.



</td>
</tr>
<tr>
<td valign="top">

*<currently\_waited\_for\>*



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

A comma-separated list of connection IDs for connections that are currently waiting for a semaphore or that are currently blocked on a mutex.



</td>
</tr>
</table>



## Remarks

None



## Privileges

Requires EXECUTE object-level privilege on the procedure, along with the MONITOR and UPDATE ANY MUTEX SEMAPHORE system privileges.



## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



The following statement returns information about all of the mutexes and semaphores in the database:

```
CALL dbo.sp_list_mutexes_semaphores();
```

