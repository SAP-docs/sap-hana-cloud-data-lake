<!-- loioa25d7f6e84f21015ba7fb54d8946c51c -->

# sp\_iqmpxincstatistics System Procedure for Data Lake Relational Engine

Displays a snapshot of the aggregate statistics of internode communication \(INC\) status since instance startup as of the moment of execution.



<a name="loioa25d7f6e84f21015ba7fb54d8946c51c__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmpxincstatistics
```



<a name="loioa25d7f6e84f21015ba7fb54d8946c51c__section_lm4_ppc_fbc"/>

## Parameters

None.



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

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MANAGE ANY STATISTICS



## Side Effects

None.



<a name="loioa25d7f6e84f21015ba7fb54d8946c51c__iq_refbb_1641"/>

## Examples

This example returns one suspended and one resumed transaction:

```
CALL sp_iqmpxincstatistics;
```


<table>
<tr>
<th valign="top">

stat\_name

</th>
<th valign="top">

stat\_value

</th>
</tr>
<tr>
<td valign="top">

NumSuspendedINC

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NumResumedINC

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NumSuspendedTXNRollBackINC

</td>
<td valign="top">

0

</td>
</tr>
</table>

