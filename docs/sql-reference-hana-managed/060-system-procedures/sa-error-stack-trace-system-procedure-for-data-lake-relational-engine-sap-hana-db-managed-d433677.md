<!-- loiod4336779fbe149d788248a86b5124222 -->

# sa\_error\_stack\_trace System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the stack trace of the error that invoked the error handler.



<a name="loiod4336779fbe149d788248a86b5124222__section_gz5_gcf_pzb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE\_QUERY.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_error_stack_trace( )
```



<a name="loiod4336779fbe149d788248a86b5124222__section_e22_qx5_s1c"/>

## Result Set


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*StackLevel*

</td>
<td valign="top">

UNSIGNED SMALLINT

</td>
<td valign="top">

The line number of the stack \(1 for the top line\). The statement that generated the error has the highest number.

</td>
</tr>
<tr>
<td valign="top">

*UserName*

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the owner of the procedure or NULL if the current level is in a batch.

</td>
</tr>
<tr>
<td valign="top">

*ProcName*

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the procedure where the statement was executed, or the batch type.

</td>
</tr>
<tr>
<td valign="top">

*LineNumber*

</td>
<td valign="top">

UNSIGNED INTEGER

</td>
<td valign="top">

The line number of the call within the procedure.

</td>
</tr>
<tr>
<td valign="top">

*IsResignal*

</td>
<td valign="top">

BIT

</td>
<td valign="top">

1 if the statement is a resignal, and 0 otherwise.

</td>
</tr>
</table>



## Remarks

Each row in the result set represents a single call on the call stack of the error. If the compound statement is not part of a procedure, function, trigger, or event, the type of batch \(`<watcom_batch>` or `<tsql_batch>`\) is returned instead of the procedure name.

This function returns line numbers as found in the proc\_defn column of the SYSPROCEDURE system table for the procedure. These line numbers might differ from those of the source definition used to create the procedure.



## Privileges

You must have EXECUTE privilege on the system procedure.



## Side Effects

None.

**Related Information**  


[sa_error_stack_trace System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/8175645e6ce21014bb799dc7da2f9b46.html "Returns the stack trace of the error that invoked the error handler.") :arrow_upper_right:

