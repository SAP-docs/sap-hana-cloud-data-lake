<!-- loioa599163a84f210158a09c7f90f986ba1 -->

# Syntax Rules for Stored Procedures

Use of parentheses and quotes in stored procedure calls varies, depending on whether you enter the procedure name directly, as you can in Interactive SQL, or invoke it with a `CALL` statement.

Some variations are permitted because the product supports both data lake Relational Engine SQL and Transact-SQL syntax. If you need Transact-SQL compatibility, be sure to use Transact-SQL syntax.


<table>
<tr>
<th valign="top">

Syntax

</th>
<th valign="top">

Syntax Type

</th>
<th valign="top">

Explanation

</th>
</tr>
<tr>
<td valign="top">

<code><i class="varname">&lt;procedure_name&gt;</i> ('<i class="varname">&lt;param&gt;</i>')</code> 

</td>
<td valign="top">

Data lake Relational Engine 

</td>
<td valign="top">

Quotes are required if you enclose parameters in parentheses.

</td>
</tr>
<tr>
<td valign="top">

<code><i class="varname">&lt;procedure_name&gt;</i> '<i class="varname">&lt;param&gt;</i>'</code> 

</td>
<td valign="top">

Data lake Relational Engine 

</td>
<td valign="top">

Parentheses are optional if you enclose parameters in quotes.

</td>
</tr>
<tr>
<td valign="top">

<code><i class="varname">&lt;procedure_name&gt;</i> <i class="varname">&lt;param&gt;</i></code> 

</td>
<td valign="top">

Transact-SQL

</td>
<td valign="top">

If you omit quotes around parameters, you must also omit parentheses.

> ### Note:  
> Quotes are always required around parameters when the owner is specified. For example, assuming the owner is *<dba\>*, `sp_iqtablesize 'dba.emp1'` requires quotes around the parameters. `sp_iqtablesize emp1` does not.



</td>
</tr>
<tr>
<td valign="top">

<code><i class="varname">&lt;procedure_name&gt;</i></code> 

</td>
<td valign="top">

Data lake Relational Engine or Transact-SQL

</td>
<td valign="top">

Use this syntax if you run a procedure with no parameters directly in Interactive SQL, and the procedure has no parameters.

</td>
</tr>
<tr>
<td valign="top">

<code>call <i class="varname">&lt;procedure_name&gt;</i> (<i class="varname">&lt;param&gt;</i>='<i class="varname">&lt;value&gt;</i>')</code> 

</td>
<td valign="top">

Data lake Relational Engine 

</td>
<td valign="top">

Use this syntax to call a procedure that passes a parameter value.

</td>
</tr>
</table>

When you use Transact-SQL stored procedures, you must use the Transact-SQL syntax.

