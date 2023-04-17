<!-- loioa505dfc384f2101593cab9b531a60204 -->

# User-Supplied Hints on Join Equality Conditions

Users can specify a join algorithm preference that does not affect every join in the query.

Simple equality join predicates can be tagged with a predicate hint that allows a join preference to be specified for just that one join. If the same join has more than one join condition with a local join preference, and if those hints are not the same value, then all local preferences are ignored for that join. Local join preferences do not affect the join order chosen by the optimizer.

The values and their actions are as follows:


<table>
<tr>
<th valign="top">

Value



</th>
<th valign="top" rowspan="1">

Action



</th>
</tr>
<tr>
<td valign="top">

0



</td>
<td valign="top">

Let the optimizer choose



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

Prefer sort-merge



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

Prefer nested-loop



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

Prefer nested-loop push-down



</td>
</tr>
<tr>
<td valign="top">

4



</td>
<td valign="top">

Prefer hash



</td>
</tr>
<tr>
<td valign="top">

5



</td>
<td valign="top">

Prefer hash push-down



</td>
</tr>
<tr>
<td valign="top">

6



</td>
<td valign="top">

Prefer asymmetric sort-merge join



</td>
</tr>
<tr>
<td valign="top">

7



</td>
<td valign="top">

Prefer sort-merge push-down



</td>
</tr>
<tr>
<td valign="top">

8



</td>
<td valign="top">

Prefer asymmetric sort-merge push-down join



</td>
</tr>
<tr>
<td valign="top">

9



</td>
<td valign="top">

Prefer partitioned hash join if the join keys include all the partition keys of a hash partitioned table



</td>
</tr>
<tr>
<td valign="top">

10



</td>
<td valign="top">

Prefer partitioned hash-push down join if the join keys include all the partition keys of a hash partitioned table



</td>
</tr>
<tr>
<td valign="top">

11



</td>
<td valign="top">

Prefer partitioned sort-merge join if the join keys include all the partition keys of a hash partitioned table



</td>
</tr>
<tr>
<td valign="top">

12



</td>
<td valign="top">

Prefer partitioned sort-merge push-down join if the join keys include all the partition keys of a hash partitioned table



</td>
</tr>
<tr>
<td valign="top">

\-1



</td>
<td valign="top">

Avoid sort-merge



</td>
</tr>
<tr>
<td valign="top">

\-2



</td>
<td valign="top">

Avoid nested-loop



</td>
</tr>
<tr>
<td valign="top">

\-3



</td>
<td valign="top">

Avoid nested-loop push-down



</td>
</tr>
<tr>
<td valign="top">

\-4



</td>
<td valign="top">

Avoid hash



</td>
</tr>
<tr>
<td valign="top">

\-5



</td>
<td valign="top">

Avoid hash push-down



</td>
</tr>
<tr>
<td valign="top">

\-6



</td>
<td valign="top">

Avoid asymmetric sort-merge join



</td>
</tr>
<tr>
<td valign="top">

\-7



</td>
<td valign="top">

Avoid sort-merge push-down



</td>
</tr>
<tr>
<td valign="top">

\-8



</td>
<td valign="top">

Avoid asymmetric sort-merge push-down join



</td>
</tr>
<tr>
<td valign="top">

\-9



</td>
<td valign="top">

Avoid partitioned hash join if the join keys include all the partition keys of a hash partitioned table



</td>
</tr>
<tr>
<td valign="top">

10



</td>
<td valign="top">

Avoid partitioned hash-push down join if the join keys include all the partition keys of a hash partitioned table



</td>
</tr>
<tr>
<td valign="top">

11



</td>
<td valign="top">

Avoid partitioned sort-merge join if the join keys include all the partition keys of a hash partitioned table



</td>
</tr>
<tr>
<td valign="top">

12



</td>
<td valign="top">

Avoid partitioned sort-merge push-down join if the join keys include all the partition keys of a hash partitioned table



</td>
</tr>
</table>



## Example

The following example requests a hash join:

```
AND (T.X = 10 * R.x, 'J:4')
```

**Related Information**  


[JOIN\_PREFERENCE Option for Data Lake Relational Engine](../090-database-options/join-preference-option-for-data-lake-relational-engine-a63bb2e.md "Controls the choice of algorithms when processing joins.")

