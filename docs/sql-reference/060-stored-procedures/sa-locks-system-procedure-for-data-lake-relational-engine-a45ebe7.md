<!-- loioa45ebe7284f210158f47fd12eed9b3b5 -->

# sa\_locks System Procedure for Data Lake Relational Engine

Displays all locks \(including mutexes\) in the database.



<a name="loioa45ebe7284f210158f47fd12eed9b3b5__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_locks( 
    [ <connection> 
    [, <creator> 
    [, <table_name> 
    [, <max_locks>
    [, <object_type> ] ] ] ] )
```



## Parameters


<dl>
<dt><b>

*<connection\>*

</b></dt>
<dd>

This INTEGER parameter specifies a connection ID number. The procedure returns lock information only about the specified connection. The default value is 0 \(or NULL\), in which case information is returned about all connections.



</dd><dt><b>

*<creator\>*

</b></dt>
<dd>

This CHAR\(128\) parameter specifies a user ID. The procedure returns information only about the tables owned by the specified user. The default value for the creator parameter is NULL. When this parameter is set to NULL, sa\_locks returns the following information:

-   If *<table\_name\>* is unspecified – locking information is returned for all tables in the database
-   If *<table\_name\>* is specified – locking information is returned for tables with the specified name that were created by the current user



</dd><dt><b>

*<table\_name\>*

</b></dt>
<dd>

This CHAR\(128\) parameter specifies a table name. The procedure returns information only about the specified tables. The default value is NULL, in which case information is returned about all tables.



</dd><dt><b>

*<max\_locks\>*

</b></dt>
<dd>

This INTEGER parameter specifies the maximum number of locks for which to return information. The default value is 1000. The value -1 means return all lock information



</dd><dt><b>

*<object\_type\>*

</b></dt>
<dd>

This CHAR\(5\) parameter limits your results to the type of object associated with the lock. Specify *ALL* to return lock information for all object types. Specify *TABLE* to return lock information for tables, global temporary tables, and materialized views. Specify *MUTEX* to return mutex information. If you do not specify *<object\_type\>*, the procedure returns lock information for all object types.



</dd>
</dl>



<a name="loioa45ebe7284f210158f47fd12eed9b3b5__section_yg1_khs_mbb"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

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

`conn_name`

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

`conn_id`

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The connection ID number.

</td>
</tr>
<tr>
<td valign="top">

`user_id`

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The user ID for the connection.

</td>
</tr>
<tr>
<td valign="top">

`table_type`

</td>
<td valign="top">

CHAR\(6\)

</td>
<td valign="top">

The type of table. This type is either BASE for a table, GLBTMP for global temporary table, or MVIEW for a materialized view.

</td>
</tr>
<tr>
<td valign="top">

`creator`

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

`table_name`

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The table on which the lock is held.

</td>
</tr>
<tr>
<td valign="top">

`index_id`

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The index ID or NULL.

</td>
</tr>
<tr>
<td valign="top">

`lock_class`

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

`lock_duration`

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

`lock_type`

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

`row_identifier`

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The identifier for the row. This is either an 8-byte row identifier or NULL.

</td>
</tr>
</table>



<a name="loioa45ebe7284f210158f47fd12eed9b3b5__section_hr2_hjs_mbb"/>

## Remarks

The `sa_locks` procedure returns a result set containing information about all the locks in the database. The value in the `lock_type` column depends on the lock classification in the `lock_class` column. The following values can be returned:


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

A position lock can be associated with a sequential table scan, or an index scan. The index\_id column indicates whether the position lock is associated with a sequential scan. If the position lock is held because of a sequential scan, the index\_id column is NULL. If the position lock is held as the result of a specific index scan, the index identifier of that index is listed in the index\_id column. The index identifier corresponds to the primary key of the ISYSIDX system table, which can be viewed using the SYSIDX view. If the position lock is held for scans over all indexes, the index ID value is -1.

The result set of the sa\_locks system procedure contains the row\_identifier column that allows you to identify the row in a table the lock refers to. It may not be necessary to specify the WITH NOLOCK clause; however, if the query is issued at isolation levels other than 0, the query may block until the locks are released, which reduces the usefulness of this method of checking.



## Privileges

Require all of the following:

-   EXECUTE object-level privilege on this procedure
-   MONITOR system privilege



<a name="loioa45ebe7284f210158f47fd12eed9b3b5__section_j43_trs_mbb"/>

## Side Effects

None.



## Examples

This example returns the locks that are currently held in the database, including information about the connection holding the lock, the lock duration, and the lock type.

```
CALL sa_locks( ); 
```


<table>
<tr>
<th valign="top">

conn\_

name

</th>
<th valign="top">

conn\_id

</th>
<th valign="top">

user\_id

</th>
<th valign="top">

table\_

type

</th>
<th valign="top">

creator

</th>
<th valign="top">

table\_name

</th>
<th valign="top">

index\_

id

</th>
<th valign="top">

lock\_

class

</th>
<th valign="top">

lock\_

duration

</th>
<th valign="top">

lock\_

type

</th>
<th valign="top">

row\_

identifier

</th>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

540620

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

BASE

</td>
<td valign="top">

dbo

</td>
<td valign="top">

iqmonSystemOverview

</td>
<td valign="top">

NULL

</td>
<td valign="top">

Schema

</td>
<td valign="top">

Transaction

</td>
<td valign="top">

Shared

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

540621

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

BASE

</td>
<td valign="top">

dbo

</td>
<td valign="top">

iqmonSystemOverview

</td>
<td valign="top">

NULL

</td>
<td valign="top">

Schema

</td>
<td valign="top">

Transaction

</td>
<td valign="top">

Shared

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

540620

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

BASE

</td>
<td valign="top">

dbo

</td>
<td valign="top">

iqmonThreadManager

</td>
<td valign="top">

NULL

</td>
<td valign="top">

Schema

</td>
<td valign="top">

Transaction

</td>
<td valign="top">

Shared

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

540621

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

BASE

</td>
<td valign="top">

dbo

</td>
<td valign="top">

iqmonThreadManager

</td>
<td valign="top">

NULL

</td>
<td valign="top">

Schema

</td>
<td valign="top">

Transaction

</td>
<td valign="top">

Shared

</td>
<td valign="top">

NULL

</td>
</tr>
</table>

This example executes a query that joins the results of the sa\_locks system procedure to a particular table by using the ROWID of the table in the join predicate.

```
SELECT S.conn_id, S.user_id, S.lock_class, S.lock_type, E.* 
  FROM sa_locks() S JOIN Employees E WITH( NOLOCK ) 
     ON ROWID(E) = S.row_identifier 
  WHERE S.table_name = 'Employees';
```

