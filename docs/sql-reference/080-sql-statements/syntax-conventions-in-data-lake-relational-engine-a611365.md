<!-- loioa611365484f210159142a347d155e080 -->

# Syntax Conventions in Data Lake Relational Engine

Conventions used in the SQL syntax descriptions.


<dl>
<dt><b>

Keywords

</b></dt>
<dd>

All SQL keywords appear in UPPERCASE; however, SQL keywords are case-insensitive, so you can type keywords in any case. For example, SELECT is the same as Select, which is the same as select.



</dd><dt><b>

Placeholders

</b></dt>
<dd>

Items that must be replaced with appropriate identifiers or expressions are shown in *<italics\>*.



</dd><dt><b>

Continuation

</b></dt>
<dd>

Lines beginning with an ellipsis \( … \) are a continuation from the previous line.



</dd><dt><b>

Optional portions

</b></dt>
<dd>

Optional portions of a statement are enclosed by square brackets. For example:

```
RELEASE SAVEPOINT [ savepoint-name ]
```

This example indicates that the *<savepoint-name\>* is optional. Do not type the square brackets.



</dd><dt><b>

Repeating items

</b></dt>
<dd>

Lists of repeating items are shown with an element of the list followed by an ellipsis. One or more list elements are allowed. When more than one is specified, they must be separated by commas if indicated as such. For example:

```
UNIQUE ( column-name [ , ... ] )
```

The example indicates that you can specify *<column-name\>* more than once, separated by commas. Do not type the square brackets.



</dd>
</dl>


<dl>
<dt><b>

Alternatives

</b></dt>
<dd>

When one option must be chosen, the alternatives are enclosed in curly braces. For example:

```
[ QUOTES { ON | OFF } ] 
```

The example indicates that if you choose the QUOTES option, you must provide one of ON or OFF. Do not type the braces.



</dd><dt><b>

One or more options

</b></dt>
<dd>

If you choose more than one, separate your choices by commas. For example:

```
{ CONNECT, DBA, RESOURCE }
```



</dd>
</dl>

