<!-- loioa6224c9a84f210159740e7ada0c238be -->

# PUT Statement \[ESQL\] for Data Lake Relational Engine

Inserts a row into the specified cursor.



<a name="loioa6224c9a84f210159740e7ada0c238be__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
PUT <cursor-name> 
   [ { USING DESCRIPTOR <sqlda-name> 
     | FROM <hostvar-list> ] [ INTO { DESCRIPTOR <into-sqlda-name> 
     | <into-hostvar-list> } ] [ ARRAY :<nnn> ] } ];
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa6224c9a84f210159740e7ada0c238be__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<cursor-name\>*

</b></dt>
<dd>

Identifier or hostvar



</dd><dt><b>

*<sqlda-name\>*

</b></dt>
<dd>

Identifier



</dd><dt><b>

*<into-sqlda-name\>*

</b></dt>
<dd>

May contain indicator variables



</dd><dt><b>

ARRAY

</b></dt>
<dd>

Can be used to carry out wide puts, which insert more than one row at a time and which might improve performance. The value *<nnn\>* is the number of rows to be inserted. The SQLDA must contain *<nnn\>* \* \(columns per row\) variables. The first row is placed in SQLDA variables 0 to \(columns per row\) - 1, and so on.

> ### Note:  
> For scroll \(values-sensitive\) cursors, the inserted row appears if the new row matches the WHERE clause and the keyset cursor has not finished populating. For dynamic cursors, if the inserted row matches the WHERE clause, the row might appear. Insensitive cursors cannot be updated.



</dd>
</dl>



<a name="loioa6224c9a84f210159740e7ada0c238be__IQ_Usage"/>

## Remarks

Inserts a row into the named cursor. Values for the columns are taken from the first SQLDA or the host variable list, in a one-to-one correspondence with the columns in the `INSERT` statement \(for an INSERT cursor\) or the columns in the select list \(for a SELECT cursor\).

The `PUT` statement can be used only on a cursor over an `INSERT` or `SELECT` statement that references a single table in the FROM clause, or that references an updatable view consisting of a single base table.

If the sqldata pointer in the SQLDA is the null pointer, no value is specified for that column. If the column has a DEFAULT VALUE associated with it, that is used; otherwise, a NULL value is used.

The second SQLDA or host variable list contains the results of the `PUT` statement.

For information on putting `LONG VARCHAR` or `LONG BINARY` values into the database, see *SET statement \[ESQL\]*.

Side Effects

-   When inserting rows into a value-sensitive \(keyset-driven\) cursor, the inserted rows appear at the end of the result set, even when they do not match the WHERE clause of the query or if an ORDER BY clause would normally have placed them at another location in the result set.



<a name="loioa6224c9a84f210159740e7ada0c238be__IQ_Permissions"/>

## Privileges

Requires the INSERT object-level privilege.

See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges



<a name="loioa6224c9a84f210159740e7ada0c238be__IQ_Side_Effects"/>

## Side Effects

Automatic commit



<a name="loioa6224c9a84f210159740e7ada0c238be__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by Open Client/Open Server



<a name="loioa6224c9a84f210159740e7ada0c238be__IQ_Examples"/>

## Examples

The following example uses `PUT` in Embedded SQL:

```
EXEC SQL PUT cur_employee FROM :EmployeeID, :Surname;
```

**Related Information**  


[DELETE \(Positioned\) Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](delete-positioned-statement-esql-sp-for-data-lake-relational-engine-a61b84a.md "Deletes the data at the current location of a cursor.")

[INSERT Statement for Data Lake Relational Engine](insert-statement-for-data-lake-relational-engine-a61fdef.md "Inserts a single row or a selection of rows, from elsewhere in the current database, into the table. This command can also insert a selection of rows from another database into the table.")

[SET Statement \[ESQL\] for Data Lake Relational Engine](set-statement-esql-for-data-lake-relational-engine-a62516a.md "Assigns a value to a SQL variable.")

[UPDATE Statement for Data Lake Relational Engine](update-statement-for-data-lake-relational-engine-a628441.md "Modifies existing rows of a single table, or a view that contains only one table.")

[UPDATE \(Positioned\) Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](update-positioned-statement-esql-sp-for-data-lake-relational-engine-a628749.md "Modifies the data at the current location of a cursor.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

