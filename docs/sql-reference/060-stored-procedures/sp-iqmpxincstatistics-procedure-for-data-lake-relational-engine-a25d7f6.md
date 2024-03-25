<!-- loioa25d7f6e84f21015ba7fb54d8946c51c -->

# sp\_iqmpxincstatistics Procedure for Data Lake Relational Engine

Displays a snapshot of the aggregate statistics of internode communication \(INC\) status since instance startup as of the moment of execution.



<a name="loioa25d7f6e84f21015ba7fb54d8946c51c__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmpxincstatistics
```



<a name="loioa25d7f6e84f21015ba7fb54d8946c51c__iq_refbb_1637"/>

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

stat\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

INC statistics name. Valid stat\_name values are:

-   NumSuspendedINC – Number of suspended INC connections since server startup
-   NumResumedINC – Number of resumed INC connections since server startup
-   NumDroppedSuspendedINC – Number of dropped INC connections that have been suspended \(on coordinator only\)
-   NumSuspendedTxnRollbackINC – Number of rolled back global DML transactions because of INC failure \(on writer only\)



</td>
</tr>
<tr>
<td valign="top">

stat\_value

</td>
<td valign="top">

UNSIGNED INTEGER

</td>
<td valign="top">

INC statistics value.

</td>
</tr>
</table>



<a name="loioa25d7f6e84f21015ba7fb54d8946c51c__iq_refbb_1638"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with the MANAGE ANY STATISTICS system privilege.



## Side Effects

None



<a name="loioa25d7f6e84f21015ba7fb54d8946c51c__iq_refbb_1641"/>

## Examples

The following example shows one suspended and one resumed transaction:

```
sp_iqmpxincstatistics;
```

```
 stat_name                   stat_value
NumSuspendedINC             1
NumResumedINC               1
NumSuspendedTXNRollBackINC  0
```

