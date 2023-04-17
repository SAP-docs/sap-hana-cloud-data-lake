<!-- loio3be02a886c5f1014a1fc9fd6600eeb9d -->

# sasql\_set\_option

Sets the value of the specified option on the specified connection.



```
bool sasql_set_option( sasql_conn <$conn>, string <$option>, mixed <$value> )
```



## Parameters

$conn
:   The connection resource returned by a connect function.

$option
:   The name of the option you want to set.

$value
:   The new option value.



## Returns

TRUE on success or FALSE on failure.



## Remarks

You can set the value for the following options:


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Description



</th>
<th valign="top">

Default



</th>
</tr>
<tr>
<td valign="top">

auto\_commit



</td>
<td valign="top">

When this option is set to on, the database server commits after executing each statement.



</td>
<td valign="top">

on



</td>
</tr>
<tr>
<td valign="top">

row\_counts



</td>
<td valign="top">

When this option is set to FALSE, the sasql\_num\_rows function returns an estimate of the number of rows affected. To obtain an exact count, set this option to TRUE.



</td>
<td valign="top">

FALSE



</td>
</tr>
<tr>
<td valign="top">

verbose\_errors



</td>
<td valign="top">

When this option is set to TRUE, the PHP driver returns verbose errors. When this option is set to FALSE, you must call the sasql\_error or sasql\_errorcode functions to get further error information.



</td>
<td valign="top">

TRUE



</td>
</tr>
</table>

You can change the default value for an option by including the following line in the `php.ini` file. In this example, the default value is set for the auto\_commit option.

```
sqlanywhere.auto_commit=0
```

