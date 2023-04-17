<!-- loio3c0ca4ba6c5f10148910a71b484b291e -->

# SABulkCopyOptions Enumeration

A bitwise flag that specifies one or more options to use with an instance of SABulkCopy.



Visual Basic
:   ```
Public Enum SABulkCopyOptions
```

C\#
:   ```
enum SABulkCopyOptions
```



## Members


<table>
<tr>
<th valign="top">

Member name



</th>
<th valign="top">

Description



</th>
<th valign="top">

Value



</th>
</tr>
<tr>
<td valign="top">

Default



</td>
<td valign="top">

Specifying only this value causes the default behavior to be used.

By default, triggers are enabled.



</td>
<td valign="top">

0x0



</td>
</tr>
<tr>
<td valign="top">

DoNotFireTriggers



</td>
<td valign="top">

When specified, triggers are not fired.

Disabling triggers requires DBA permission. Triggers are disabled for the connection at the start of WriteToServer and the value is restored at the end of the method.



</td>
<td valign="top">

0x1



</td>
</tr>
<tr>
<td valign="top">

KeepIdentity



</td>
<td valign="top">

When specified, the source values to be copied into an identity column are preserved.

By default, new identity values are generated in the destination table.



</td>
<td valign="top">

0x2



</td>
</tr>
<tr>
<td valign="top">

TableLock



</td>
<td valign="top">

When specified the table is locked using the command LOCK TABLE table\_name WITH HOLD IN SHARE MODE.

This lock is in place until the connection is closed.



</td>
<td valign="top">

0x4



</td>
</tr>
<tr>
<td valign="top">

UseInternalTransaction



</td>
<td valign="top">

When specified, each batch of the bulk-copy operation is executed within a transaction.

When not specified, transaction aren't used. If you indicate this option and also provide an SATransaction object to the constructor, then a System.ArgumentException occurs.



</td>
<td valign="top">

0x8



</td>
</tr>
</table>



## Remarks

The SABulkCopyOptions enumeration is used when you construct an SABulkCopy object to specify how the WriteToServer methods behave.

The CheckConstraints and KeepNulls options are not supported.

**Related Information**  


[SABulkCopy Class](sabulkcopy-class-3c0d810.md "Efficiently bulk load a database table with data from another source.")

