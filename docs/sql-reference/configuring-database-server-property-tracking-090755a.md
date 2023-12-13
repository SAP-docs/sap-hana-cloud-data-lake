<!-- loio090755a287fe4fb7aed66c6df5877fa1 -->

# Configuring Database Server Property Tracking

Configure your database server to track the values of numeric database server properties.



## Context

Only database server properties with numeric values can be tracked.



## Procedure

Choose one or both of the following options:


<table>
<tr>
<th valign="top">

Option

</th>
<th valign="top">

Action

</th>
</tr>
<tr>
<td valign="top">

**Specify database server properties to be tracked for the database server**

</td>
<td valign="top">

Use the sa\_server\_option system procedure to configure property tracking for the database server. For example, execute the following statement:

***CALL sa\_server\_option\( 'PropertyHistoryList,ProcessCPUSystem,ProcessCPUUser,PropertyHistorySize,250K' \);***

</td>
</tr>
<tr>
<td valign="top">

**Specify database server properties to be tracked for the database**

</td>
<td valign="top">

Use the sa\_db\_option system procedure to configure property tracking of database server properties for the database. For example, execute the following statement:

***CALL sa\_db\_option\( 'PropertyHistoryList,ProcessCPUSystem,ProcessCPUUser' \);***

</td>
</tr>
</table>



## Results

The values of the specified database server properties are tracked for either the specified amount of time or until the specified maximum amount of memory has been reached.

