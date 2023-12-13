<!-- loioa5ae206484f210158d7db008e8f2fa2e -->

# sp\_iqindexuse Procedure for Data Lake Relational Engine

Reports detailed usage information for secondary \(non-FP\) indexes accessed by the workload.



<a name="loioa5ae206484f210158d7db008e8f2fa2e__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqindexuse; 
```



<a name="loioa5ae206484f210158d7db008e8f2fa2e__section_ivm_zd1_nbb"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

IndexName

</td>
<td valign="top">

Index name

</td>
</tr>
<tr>
<td valign="top">

TableName

</td>
<td valign="top">

Table name

</td>
</tr>
<tr>
<td valign="top">

Owner

</td>
<td valign="top">

User name of index owner

</td>
</tr>
<tr>
<td valign="top">

UID

</td>
<td valign="top">

Index unique identifier. UID is a number assigned by the system that uniquely identifies the instance of the index \(where instance is defined when an object is created\).

</td>
</tr>
<tr>
<td valign="top">

Type

</td>
<td valign="top">

Index type

</td>
</tr>
<tr>
<td valign="top">

LastDT

</td>
<td valign="top">

Date/time of last access

</td>
</tr>
<tr>
<td valign="top">

NOpt

</td>
<td valign="top">

Number of metadata or uniqueness accesses

</td>
</tr>
<tr>
<td valign="top">

NQry

</td>
<td valign="top">

Number of query accesses

</td>
</tr>
<tr>
<td valign="top">

NConstraint

</td>
<td valign="top">

Number of accesses for unique or referential integrity checks

</td>
</tr>
</table>



<a name="loioa5ae206484f210158d7db008e8f2fa2e__iq_refbb_1625"/>

## Remarks

Each secondary index accessed by the workload displays a row. Indexes that have not been accessed do not appear. Index usage is broken down by optimizer, constraint, and query usage.

Indexes from tables created in SYSTEM are not reported.



<a name="loioa5ae206484f210158d7db008e8f2fa2e__iq_refbb_1624"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with the MONITOR system privilege.



<a name="loioa5ae206484f210158d7db008e8f2fa2e__section_b3r_hc1_nbb"/>

## Side Effects

None



<a name="loioa5ae206484f210158d7db008e8f2fa2e__iq_refbb_1627"/>

## Examples

The following shows sample output from the sp\_iqindexuse procedure:


<table>
<tr>
<th valign="top">

IndexName

</th>
<th valign="top">

TableName

</th>
<th valign="top">

Owner

</th>
<th valign="top">

UID

</th>
<th valign="top">

Type

</th>
</tr>
<tr>
<td valign="top">

n\_nationkey\_hg

</td>
<td valign="top">

nation

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

29

</td>
<td valign="top">

HG

</td>
</tr>
<tr>
<td valign="top">

n\_regionkey\_hg

</td>
<td valign="top">

nation

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

31

</td>
<td valign="top">

HG

</td>
</tr>
<tr>
<td valign="top">

r\_regionkey\_hg

</td>
<td valign="top">

region

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

47

</td>
<td valign="top">

HG

</td>
</tr>
<tr>
<td valign="top">

s\_suppkey\_hg

</td>
<td valign="top">

supplier

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

64

</td>
<td valign="top">

HG

</td>
</tr>
<tr>
<td valign="top">

p\_partkey\_hg

</td>
<td valign="top">

part

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

87

</td>
<td valign="top">

HG

</td>
</tr>
<tr>
<td valign="top">

s\_suppkey\_hg

</td>
<td valign="top">

supplier

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

64

</td>
<td valign="top">

HG

</td>
</tr>
</table>


<table>
<tr>
<th valign="top">

LastDT

</th>
<th valign="top">

NOpt

</th>
<th valign="top">

NQry

</th>
<th valign="top">

NConstraint

</th>
</tr>
<tr>
<td valign="top">

20070917 22:08:06~

</td>
<td valign="top">

12

</td>
<td valign="top">

0

</td>
<td valign="top">

12

</td>
</tr>
<tr>
<td valign="top">

20070917 22:08:06~

</td>
<td valign="top">

12

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

20070917 22:08:06~

</td>
<td valign="top">

12

</td>
<td valign="top">

0

</td>
<td valign="top">

12

</td>
</tr>
<tr>
<td valign="top">

20070917 22:08:06~

</td>
<td valign="top">

12

</td>
<td valign="top">

0

</td>
<td valign="top">

12

</td>
</tr>
<tr>
<td valign="top">

20070917 22:08:06~

</td>
<td valign="top">

6

</td>
<td valign="top">

0

</td>
<td valign="top">

6

</td>
</tr>
<tr>
<td valign="top">

20070917 22:08:06~

</td>
<td valign="top">

12

</td>
<td valign="top">

0

</td>
<td valign="top">

12

</td>
</tr>
</table>

**Related Information**  


[sp\_iqcolumnuse Procedure for Data Lake Relational Engine](sp-iqcolumnuse-procedure-for-data-lake-relational-engine-a59fb88.md "Reports detailed usage information for columns accessed by the workload.")

[sp\_iqindexadvice Procedure for Data Lake Relational Engine](sp-iqindexadvice-procedure-for-data-lake-relational-engine-a5ab8bc.md "Displays stored index advice messages. Optionally clears advice storage.")

[sp\_iqtableuse Procedure for Data Lake Relational Engine](sp-iqtableuse-procedure-for-data-lake-relational-engine-a5bae03.md "Reports detailed usage information for tables accessed by the workload.")

[sp\_iqunusedcolumn Procedure for Data Lake Relational Engine](sp-iqunusedcolumn-procedure-for-data-lake-relational-engine-a5bbef3.md "Reports columns that were not referenced by the workload.")

[sp\_iqunusedindex Procedure for Data Lake Relational Engine](sp-iqunusedindex-procedure-for-data-lake-relational-engine-a5bc6ce.md "Reports secondary (non-FP) indexes that were not referenced by the workload.")

[sp\_iqunusedtable Procedure for Data Lake Relational Engine](sp-iqunusedtable-procedure-for-data-lake-relational-engine-a5bced3.md "Reports tables that were not referenced by the workload.")

[sp\_iqworkmon Procedure for Data Lake Relational Engine](sp-iqworkmon-procedure-for-data-lake-relational-engine-a5c13d2.md "Controls collection of workload monitor usage information, and reports monitoring collection status. sp_iqworkmon collects information only for queries (SQL statements containing a FROM clause). You cannot use sp_iqworkmon for INSERT or LOAD statements.")

