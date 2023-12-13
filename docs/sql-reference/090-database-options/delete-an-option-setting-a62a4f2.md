<!-- loioa62a4f2284f21015b21797f8c740a93c -->

# Delete an Option Setting

Omit the *<option-value\>* to delete the option setting from the database.

If *<option-value\>* is omitted, the specified option setting is deleted from the database. If *<option-value\>* is a personal option setting, the value reverts back to the `PUBLIC` setting. If a `TEMPORARY` option is deleted, the option setting reverts back to the permanent setting.

For example, reset the `ANSINULL` option to its default value:

```
SET OPTION ANSINULL =
```

If you incorrectly type the name of an option when you are setting the option, the incorrect name is saved in the `SYSOPTION` table. You can remove the incorrectly typed name from the `SYSOPTION` table by setting the option `PUBLIC` with an equality after the option name and no value:

```
SET OPTION PUBLIC.a_mistyped_name=;
```

For example, if you set an option and incorrectly type the name, you can verify that the option was saved by selecting from the `SYSOPTIONS` view:

```
SET OPTION PUBLIC.a_mistyped_name='ON';
SELECT * FROM SYSOPTIONS ORDER BY 2;
```


<table>
<tr>
<th valign="top" rowspan="1">

User Name

</th>
<th valign="top" rowspan="1">

Option

</th>
<th valign="top" rowspan="1">

Setting

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

`PUBLIC`

</td>
<td valign="top" rowspan="1">

a\_mistyped\_name

</td>
<td valign="top" rowspan="1">

ON

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

`PUBLIC`

</td>
<td valign="top" rowspan="1">

Abort\_On\_Error\_File

</td>
<td valign="top" rowspan="1">



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

`PUBLIC`

</td>
<td valign="top" rowspan="1">

Abort\_On\_Error\_Line

</td>
<td valign="top" rowspan="1">

0

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

`PUBLIC`

</td>
<td valign="top" rowspan="1">

Abort\_On\_Error\_Number

</td>
<td valign="top" rowspan="1">

0

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

...

</td>
<td valign="top" rowspan="1">



</td>
<td valign="top" rowspan="1">



</td>
</tr>
</table>

Remove the incorrectly typed option by setting the option to no value, then verify that the option is removed:

```
SET OPTION PUBLIC.a_mistyped_name=;
SELECT * FROM SYSOPTIONS ORDER BY 2;
```


<table>
<tr>
<th valign="top" rowspan="1">

User Name

</th>
<th valign="top" rowspan="1">

Option

</th>
<th valign="top" rowspan="1">

Setting

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

`PUBLIC`

</td>
<td valign="top" rowspan="1">

Abort\_On\_Error\_File

</td>
<td valign="top" rowspan="1">



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

`PUBLIC`

</td>
<td valign="top" rowspan="1">

Abort\_On\_Error\_Line

</td>
<td valign="top" rowspan="1">

0

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

`PUBLIC`

</td>
<td valign="top" rowspan="1">

Abort\_On\_Error\_Number

</td>
<td valign="top" rowspan="1">

0

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

...

</td>
<td valign="top" rowspan="1">



</td>
<td valign="top" rowspan="1">



</td>
</tr>
</table>

If you remove the `PUBLIC` option and then try to add the `USER` option, an error message displays:

```
Couldn't execute the statement.
Invalid option 'chained' -- no PUBLIC setting exists
SQLCODE=-200?ODBC 3 State="42000"
Line 1,Column 29

```

To reset the `PUBLIC` option to the default value, explicitly set the default value:

```
SET OPTION PUBLIC.chained ='ON';
```

