<!-- loioa5af357c84f21015bd5cb5d281321779 -->

# sp\_iqlocks Procedure for Data Lake Relational Engine

Shows information about locks in the database, for both the IQ main store and the IQ catalog store.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqlocks ( [ <connection>,] [ [ <owner>.]<table_name>,]
 <max_locks>,] [ <sort_order> ] )
```



<a name="loioa5af357c84f21015bd5cb5d281321779__iq_refbb_1658"/>

## Parameter

All parameters are optional to restrict results:


<dl>
<dt><b>

*<connection\>*

</b></dt>
<dd>

\(Optional\) An INTEGER parameter that specifies the connection ID. With this option, the procedure returns information about locks for the specified connection only. Default is zero, which returns information about all connections.



</dd><dt><b>

*<owner\>*.*<table\_name\>*

</b></dt>
<dd>

\(Optional\) A CHAR\(128\) parameter that specifies the table name. With this option, the procedure returns information about locks for the specified table only. Default is NULL, which returns information about all tables in the database. If you do not specify owner, it is assumed that the caller of the procedure owns the table.



</dd><dt><b>

*<max\_locks\>*

</b></dt>
<dd>

\(Optional\) An INTEGER parameter that specifies the maximum number of locks for which to return information. Default is 0, which returns all lock information.



</dd><dt><b>

*<sort\_order\>*

</b></dt>
<dd>

\(Optional\) A CHAR\(1\) parameter that specifies the order in which to return information:

-   C sorts by connection \(default\)
-   T sorts by table\_name



</dd>
</dl>



<a name="loioa5af357c84f21015bd5cb5d281321779__section_rsk_nch_nbb"/>

## Returns

sp\_iqlocks displays the following information, sorted as specified in the *<sort\_order\>* parameter:


<table>
<tr>
<th valign="top">

Column



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

conn\_name



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

The name of the current connection.



</td>
</tr>
<tr>
<td valign="top">

conn\_id



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Connection ID that has the lock.



</td>
</tr>
<tr>
<td valign="top">

user\_id



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

User associated with this connection ID.



</td>
</tr>
<tr>
<td valign="top">

table\_type



</td>
<td valign="top">

CHAR\(6\)



</td>
<td valign="top">

The type of table. This type is either BASE for a table, GLBTMP for global temporary table, or MVIEW for a materialized view. Materialized views are only supported for SAP SQL Anywhere tables in the data lake Relational Engine catalog store.



</td>
</tr>
<tr>
<td valign="top">

creator



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

The owner of the table.



</td>
</tr>
<tr>
<td valign="top">

table\_name



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

Table on which the lock is held.



</td>
</tr>
<tr>
<td valign="top">

index\_id



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

The index ID or NULL



</td>
</tr>
<tr>
<td valign="top">

lock\_class



</td>
<td valign="top">

CHAR\(8\)



</td>
<td valign="top">

The lock class. One of Schema, Row, Table, or Position.



</td>
</tr>
<tr>
<td valign="top">

lock\_duration



</td>
<td valign="top">

CHAR\(11\)



</td>
<td valign="top">

The duration of the lock. One of Transaction, Position, or Connection.



</td>
</tr>
<tr>
<td valign="top">

lock\_type



</td>
<td valign="top">

CHAR\(9\)



</td>
<td valign="top">

The lock type \(this is dependent on the lock class\).



</td>
</tr>
<tr>
<td valign="top">

row\_identifier



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The identifier for the row the lock starts on, or NULL.



</td>
</tr>
<tr>
<td valign="top">

row\_range



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

The number of contiguous rows that are locked.



</td>
</tr>
</table>



<a name="loioa5af357c84f21015bd5cb5d281321779__iq_refbb_1659"/>

## Remarks

Displays information about current locks in the database. Depending on the options you specify, you can restrict results to show locks for a single connection, a single table, or a specified number of locks.

If sp\_iqlocks cannot find the connection ID or user name of the user who has a lock on a table, it displays a 0 \(zero\) for the connection ID and `User unavailable` for the user name.

The value in the lock\_type column depends on the lock classification in the lock\_class column. The following values can be returned:


<table>
<tr>
<th valign="top">

Lock Class



</th>
<th valign="top">

Lock Types



</th>
<th valign="top">

Comments



</th>
</tr>
<tr>
<td valign="top">

Schema



</td>
<td valign="top">

-   Shared – shared schema lock
-   Exclusive – \(data lake Relational Engine catalog store tables only\) exclusive schema lock



</td>
<td valign="top">

For schema locks, the row\_identifier and index ID values are NULL.



</td>
</tr>
<tr>
<td valign="top">

Row



</td>
<td valign="top">

-   Read – read lock
-   Intent – intent lock
-   ReadPK – read lock
-   Write – write lock
-   WriteNoPK – write lock
-   Surrogate – surrogate lock



</td>
<td valign="top">

Row read locks can be short-term locks \(scans at isolation level 1\) or long-term locks at higher isolation levels. The lock\_duration column indicates whether the read lock is of short duration because of cursor stability \(Position\) or long duration, held until COMMIT/ROLLBACK \(Transaction\). Row locks are always held on a specific row that has an 8-byte row identifier that is reported as a 64-bit integer value in the row\_identifier column.

A surrogate lock is a special case of a row lock. Surrogate locks are held on surrogate entries, which are created when referential integrity checking is delayed. There is not a unique surrogate lock for every surrogate entry created in a table. Rather, a surrogate lock corresponds to the set of surrogate entries created for a given table by a given connection. The row\_identifier value is unique for the table and connection associated with the surrogate lock.

If required, key and non-key portions of a row can be locked independently. A connection can obtain a read lock on the key portion of a row for shared \(read\) access so that other connections can still obtain write locks on other non-key columns of a row. Updating non-key columns of a row does not interfere with the insertion and deletion of foreign rows referencing that row.



</td>
</tr>
<tr>
<td valign="top">

Table



</td>
<td valign="top">

-   Shared – shared table lock
-   Intent – intent to update table lock
-   Exclusive – \(data lake Relational Engine catalog store tables only\) exclusive table lock



</td>
<td valign="top">

None



</td>
</tr>
<tr>
<td valign="top">

Position



</td>
<td valign="top">

-   Phantom – \(data lake Relational Engine catalog store tables only\) phantom lock
-   Insert – insert lock



</td>
<td valign="top">

Usually a position lock is also held on a specific row, and that row's 64-bit row identifier appears in the row\_identifier column in the result set. However, Position locks can be held on entire scans \(index or sequential\), in which case the row\_identifier column is NULL.



</td>
</tr>
</table>

> ### Note:  
> Exclusive, phantom, or anti-phantom locks can be placed on data lake Relational Engine catalog store tables, but not on data lake Relational Engine tables in the data lake Relational Engine main store. Unless you have explicitly taken out locks on a table in the catalog store, you never see these types of locks in a data lake Relational Engine database.



<a name="loioa5af357c84f21015bd5cb5d281321779__iq_refbb_1657"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with the MONITOR system privilege.



## Side Effects

None



<a name="loioa5af357c84f21015bd5cb5d281321779__iq_refbb_1660"/>

## Example

The example shows the sp\_iqlocks procedure call and its output in the data lake Relational Engine database. The procedure is called with all default options, so that the output shows all locks, sorted by connection:

```
call sp_iqlocks()
```

```
conn_name         conn_id      user_id      table_type  creator      table_name  
=========         =======      =======      ==========  =======      ==========  
SQL_DBC_13cd6038  3            HDLADMIN     BASE        HDLADMIN     rv_locks2  
SQL_DBC_13cd6038  3            HDLADMIN     BASE        HDLADMIN     rv_locks2 
SQL_DBC_13cd6038  3            HDLADMIN     BASE        HDLADMIN     rv_locks2  
RVL_CONN_T775     1000000407                BASE        HDLADMIN     rv_locks2 

index_id  lock_class  lock_duration  lock_type  row_identifier   row_range
========  ==========  =============  =========  ==============   ========= 
          Schema      Transaction    Shared                        
          Row         Transaction    Row        1                4
          Row         Transaction    Row        281474976710656  1
          Table       Transaction    Intent
```

