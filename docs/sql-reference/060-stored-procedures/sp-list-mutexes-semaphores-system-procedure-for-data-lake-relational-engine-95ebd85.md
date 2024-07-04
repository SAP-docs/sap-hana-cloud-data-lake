<!-- loio95ebd85c6ea11014aa449ce4706bbebd -->

# sp\_list\_mutexes\_semaphores System Procedure for Data Lake Relational Engine

Returns information about all temporary and permanent mutexes and semaphores, including which connection is holding each mutex and whether a semaphore is being waited for.



```
sp_list_mutexes_semaphores
```



<a name="loio95ebd85c6ea11014aa449ce4706bbebd__section_obc_v1j_yyb"/>

## Parameters

None.



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

None.



## Privileges

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MONITOR system privilege
-   UPDATE ANY MUTEX SEMAPHORE system privilege



## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



<a name="loio95ebd85c6ea11014aa449ce4706bbebd__section_ed2_yfk_yyb"/>

## Examples

This example returns information about all mutexes and semaphores in the database:

```
CALL sp_list_mutexes_semaphores();
```


<table>
<tr>
<th valign="top">

mutex\_

semaphore\_

id

</th>
<th valign="top">

creator

</th>
<th valign="top">

name

</th>
<th valign="top">

type

</th>
<th valign="top">

is\_

temp

</th>
<th valign="top">

is\_

temp

</th>
<th valign="top">

is\_

dropped

</th>
<th valign="top">

start\_

with

</th>
<th valign="top">

current\_

count

</th>
<th valign="top">

currently\_

owned\_

by

</th>
<th valign="top">

currently\_

waited\_

for

</th>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

hdl\_telemetry\_service

</td>
<td valign="top">

telemetry\_users\_mutex

</td>
<td valign="top">

MUTEX:C

</td>
<td valign="top">

N

</td>
<td valign="top">

N

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

cg\_dbo

</td>
<td valign="top">

hdl\_container\_users\_mutex

</td>
<td valign="top">

MUTEX:C

</td>
<td valign="top">

N

</td>
<td valign="top">

N

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

cg\_dbo

</td>
<td valign="top">

hdl\_add\_missing\_container\_objects\_mutex

</td>
<td valign="top">

MUTEX:C

</td>
<td valign="top">

N

</td>
<td valign="top">

N

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
</table>

