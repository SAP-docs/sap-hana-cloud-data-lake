<!-- loio68b84729d44b4e2cbc4b4b851193995d -->

# SELECT Statement for SAP HANA Database

Queries data from the SAP HANA database.



<a name="loio68b84729d44b4e2cbc4b4b851193995d__sql_select_1sql_select_syntax"/>

## Syntax

```
<select_statement> ::= 
[ <with_clause> ] <subquery> [ <for_update> | FOR SHARE LOCK | <for_system_time> ] [ <hint_clause> ] 
 | [ <with_clause> ] ( <subquery> ) [ <for_update> | <for_json_clause> | <for_xml_clause> ] [ <hint_clause> ]
 | { <subquery> | ( <subquery> ) } INTO { <table_ref> | <variable_name_list> } [ ( <column_name_list> ) ] [ <hint_clause> ]
[ TOTAL ROWCOUNT ]

 
<subquery> ::= <select_clause> <from_clause> [ <where_clause> ]
 [ <group_by_clause> ]
 [ <having_clause> ] 
 [ <set_operator> <subquery> [ {, <set_operator> <subquery> }... ] ]
 [ <order_by_clause><limit_clause> ]  
```



<a name="loio68b84729d44b4e2cbc4b4b851193995d__sql_select_1sql_select_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<with\_clause\>*

</b></dt>
<dd>

Specifies an output of the subquery to be stored in a temporary result set named *<query\_name\>*.

```
<with_clause> ::= WITH <with_list_element> [ {, <with_list_element>  }... ]

<with_list_element> ::= <query_name> [ <column_list_clause> ] AS ( <subquery> )

<query_name> ::= <identifier>

<column_list_clause> ::= ( <column_name>, ... )

<column_name> ::= <identifier>
```

The query name is an alias of the *<subquery\>* and it should be unique within the *<with\_clause\>*. The *<with\_clause\>* cannot support recursive query expressions.

The list of column identifiers is ordered according to the order of values in the *<subquery\>*. The column list can be omitted.



</dd><dt><b>

*<for\_update\>*

</b></dt>
<dd>

Locks the selected records so that other users cannot lock or change the records until the end of this transaction.

```
<for_update> ::= FOR UPDATE [ OF <update_column_name_list> ] [ <wait_nowait> ] 
   [ IGNORE LOCKED ]

<wait_nowait> ::= { WAIT <unsigned_integer> | NOWAIT }

<update_column_name_list>> ::= ( <column_name> [, <column_name>...] )
```

FOR UPDATE supports row, column, and virtual tables created from HANA remote sources and can be used with either one or more column table, or a row table.

If a HANA query using virtual tables cannot be entirely delegated to the remote source, the query returns the error message indicating that the FOR UPDATE feature is not supported.


<dl>
<dt><b>

*<wait\_nowait\>*

</b></dt>
<dd>

Specifies when to return an error if a lock cannot be obtained on a record. If WAIT *<unsigned\_integer\>* is specified, then the statement waits up to the specified number of seconds for each record. If the statement fails to acquire a lock after waiting, then it returns an error message indicating a timeout. If NOWAIT is specified, and the statement fails to acquire record locks, then an error is returned indicating that the resource is busy. WAIT 0 is equivalent to NOWAIT. If *<wait\_nowait\>* is not specified, then the default behavior reflects the lock\_wait\_timeout transaction timeout setting located in `indexserver.ini`.



</dd><dt><b>

IGNORE LOCKED

</b></dt>
<dd>

Specifies to ignore locked records.

A list of columns specifies which table or view in the FROM clause should be locked. If there is only a single table or view, then FOR UPDATE is sufficient. However, if there are two objects \(such as tables, views, of subqueries\), use OF.

A table used in a subquery cannot be locked. Also only one table/view can be currently locked. The lock is released when the corresponding transaction is finished by commit or rollback.



</dd>
</dl>



</dd><dt><b>

FOR SHARE LOCK

</b></dt>
<dd>

Acquires shared locks on the queried records. By doing so, the locked records stay intact until the transaction is committed or rolled back. If a queried record is already exclusively locked by another transaction, the SELECT FOR SHARE LOCK statement waits for the lock to be released, or waits for the current transaction’s lock-wait-timeout value, whichever is shorter.



</dd><dt><b>

*<for\_json\_clause\>*

</b></dt>
<dd>

Returns a results set as a JSON document.

```
<for_json_clause> ::= FOR JSON [ ( <json_option_string_list> ) ]
    [ <json_return_clause> ]
```

The *<for\_json\_clause\>* clause is supported in table subqueries \(for example, SELECT...FROM \(SELECT...FROM mytable FOR JSON\);\) and scalar subqueries \(for example, SELECT \(SELECT…FROM myTable FOR JSON\) FROM s;\), as well inside INSERT INTO and FOR UPDATE subqueries.


<dl>
<dt><b>

*<json\_option\_string\_list\>*

</b></dt>
<dd>

Sets options for the resulting JSON

```
<json_option_string_list> ::= '<json_basic_string_expression>' [,...]
```

*<json\_basic\_string\_expression\>* is a comma-separated string of option-value pairs. The following table defines the options and what they control.


<table>
<tr>
<th valign="top">

Option



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

format



</td>
<td valign="top">

Whether to insert newline and tab for elements. Possible values are 'yes' or 'no' \(the default\).



</td>
</tr>
<tr>
<td valign="top">

omitnull



</td>
<td valign="top">

Whether to omit NULL value records in the result JSON document. Possible values are 'yes' \(the default\), or 'no'.



</td>
</tr>
<tr>
<td valign="top">

arraywrap



</td>
<td valign="top">

Whether to include \[ \] at the beginning and end of the JSON document. Possible values are 'yes' \(the default\), or 'no'.



</td>
</tr>
</table>



</dd><dt><b>

*<json\_return\_clause\>*

</b></dt>
<dd>

Specifies the return type of the results. The default is NCLOB.

```
<json_returns_clause> ::=  RETURNS { NVARCHAR ( <integer> ) | NCLOB }
```



</dd>
</dl>



</dd><dt><b>

*<for\_xml\_clause\>*

</b></dt>
<dd>

Returns a result set as an XML document.

```
<for_xml_clause> ::= FOR XML [ ( <xml_option_string_list> ) ] [ <xml_returns_clause> ]
```

The *<for\_xml\_clause\>* clause is supported in table subqueries \(for example, SELECT...FROM \(SELECT...FROM mytable FOR XML\);\) and scalar subqueries \(for example, SELECT \(SELECT…FROM myTable FOR XML\) FROM s;\), as well inside INSERT INTO and FOR UPDATE subqueries.


<dl>
<dt><b>

*<xml\_option\_string\_list\>*

</b></dt>
<dd>

Sets options for the resulting XML.

```
<xml_option_string_list> ::= '<xml_basic_string_expression>' [,...]
```

*<xml\_basic\_string\_expression\>* is a comma-separated string of option-value pairs. The following table defines the options and what they control.


<table>
<tr>
<th valign="top">

Option



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

columnstyle



</td>
<td valign="top">

The representation of SQL columns. Possible values are 'element' \(the default\), or 'attribute'.



</td>
</tr>
<tr>
<td valign="top">

format



</td>
<td valign="top">

Whether to insert newline and tab for elements. Possible values are 'yes' \(the default\), or 'no'.



</td>
</tr>
<tr>
<td valign="top">

header



</td>
<td valign="top">

Whether to include the XML declaration header \(<?xml version="1.0"?\>\). Possible values are 'yes', or 'no' \(the default\).



</td>
</tr>
<tr>
<td valign="top">

incremental



</td>
<td valign="top">

Whether to return a single row or multiple rows. Possible values are 'yes', or 'no' \(the default\).



</td>
</tr>
<tr>
<td valign="top">

nullstyle



</td>
<td valign="top">

Whether to omit or present a null attribute for NULL values. Possible values are 'omit' \(the default\), or 'attribute'.



</td>
</tr>
<tr>
<td valign="top">

root



</td>
<td valign="top">

Whether to include a root element for the table name. Possible values are 'yes' \(the default\), or 'no'



</td>
</tr>
<tr>
<td valign="top">

rowname



</td>
<td valign="top">

Sets the name of the row element. The default is 'row'.



</td>
</tr>
<tr>
<td valign="top">

schemaloc



</td>
<td valign="top">

Sets the *<schemalocation\>* value in the root element. If the *<root\>* option is set to no, then this option is ignored. This value is a string with a URI.



</td>
</tr>
<tr>
<td valign="top">

tablename



</td>
<td valign="top">

Names the root element. If the root option is set to 'no', then this option is ignored. The value is a string and the default is 'resultset'.



</td>
</tr>
<tr>
<td valign="top">

targetns



</td>
<td valign="top">

Sets the *<targetnamespace\>* value in the root element. If the *<root\>* option is set to 'no', then this option is ignored.



</td>
</tr>
</table>



</dd><dt><b>

*<returns\_clause\>*

</b></dt>
<dd>

Specifies the return type of the results. The default is NCLOB.

```
<returns_clause> ::=  RETURNS { NVARCHAR ( <integer> ) | NCLOB }
```



</dd>
</dl>



</dd><dt><b>

*<hint\_clause\>*

</b></dt>
<dd>

Specifies a hint to use for the query.

```
<hint_clause> ::= 
 WITH HINT( <hint_element> [, <hint_element> … ] )

<hint_element> ::= 
 { <hint> | <hint_with_parameters> }

<hint> ::= !! hint_name from public hint list

<hint_with_parameters> ::= 
 ROUTE_TO( <volume_id> [ {, <volume_id> } ] ) 
 | NO_ROUTE_TO( <volume_id> [ {, <volume_id> } ] ) 
 | ROUTE_BY( <table_name> [ {, <table_name> } ] ) 
 | ROUTE_BY_CARDINALITY( <table_name> [ {, <table_name> } ] ) 
 | DATA_TRANSFER_COST ( { 0 | 1 } )
```

When there are hint clauses in the subquery, only the most outer hint is applied.

Incorrect syntax or semantics generate an SQL error.



</dd><dt><b>

*<select\_clause\>*

</b></dt>
<dd>

Specifies an output to be returned either to the caller or to an outer *<select\_clause\>* if one exists.

```
<select_clause> ::= 
 SELECT [ TOP <unsigned_integer> ] [ ALL | DISTINCT ] <select_list>
```


<dl>
<dt><b>

TOP

</b></dt>
<dd>

Specifies that the first *<unsigned\_integer\>* records from the SQL statement should be returned.

```
TOP <unsigned_integer>
```



</dd><dt><b>

DISTINCT

</b></dt>
<dd>

Specifies that only one copy of each set of duplicate records selected should be returned.



</dd><dt><b>

ALL

</b></dt>
<dd>

Specifies that all rows selected, including all copies of duplicates should be returned. This is the default option.



</dd><dt><b>

*<select\_list\>*

</b></dt>
<dd>

Specifies the select items that are in scope for the query.

```
<select_list> ::= <select_item>[ {, <select_item> }... ]

<select_item> ::=
 { <column_name> | <expression> | <association_expression> } [ AS <alias> ]
 | [ <table_name>.] 
```


<dl>
<dt><b>

*<select\_item\>*

</b></dt>
<dd>

Specifies the details of the columns to be retrieved.



</dd><dt><b>

*<table\_name\>*

</b></dt>
<dd>

Specifies the table that is the source for the selected columns, with the optional schema name.

For linked database, *<database\_name\>* is the name of the remote source. *<identifier\>* is the name of the table on the remote source.



</dd><dt><b>

*<asterisk\>*

</b></dt>
<dd>

\(\*\) selects all columns from all tables or views listed in the *<from\_clause\>*. If you provide a schema name or a table name with an asterisk \(\*\), then it limits the scope of the result set to the specified table.



</dd><dt><b>

*<alias\>*

</b></dt>
<dd>

Specifies an alias for the expression.



</dd><dt><b>

*<expression\>*

</b></dt>
<dd>

Combination of one or more values, operators, and SQL functions that evaluate to a value.



</dd><dt><b>

*<association\_expression\>*

</b></dt>
<dd>

Specifies a column association, with optional filter \(condition\) on column values.

```
<association_expression> ::= <association_ref>[.<association_ref>[...] ]

<associated_ref>::= <column_name>[[<condition> [ <association_cardinality> ] ]]

<association_cardinality> ::= USING { ONE | MANY } TO { ONE | MANY } JOIN
```

*<condition\>* applies the specified predicate, filtering the column values. For example `myTable[myColumn>100]` filters matches values of myColumn that are greater than 100. The square brackets around *<condition\>* are required syntax.

*<association\_cardinality\>* specifies the join to apply.



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<from\_clause\>*

</b></dt>
<dd>

Specifies inputs such as tables, views, and subqueries to be used as the data source for the SELECT statement.

```
<from_clause> ::= FROM <table_expression> [, <table_expression> ...]

<table_expression> ::= 
 <table_ref>  
 | <system_versioned_table_ref> 
 | <subquery>  
 | <joined_table> 
 | <lateral_table_expression>
 | <collection_derived_table>
 | <function_reference>
 | :<table_variable>
 | <associated_table_expression>
```


<dl>
<dt><b>

*<table\_expression\>*

</b></dt>
<dd>

Specifies the data source for the query.



</dd><dt><b>

*<table\_ref\>*

</b></dt>
<dd>

Specifies a table reference as a data source.

```
<table_ref> ::= <table_name> 
 [ <for_system_time> | <for_application_time_period> ]
 [ <partition_restriction> ] 
 [ [ AS ] <table_alias> ] 
 [ <tablesample_clause> ]
```


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Specifies a table as a data source.

```
<table_name> ::= [ [ <database_name>.]<schema.name>.]<identifier>
```

For linked database, *<database\_name\>* is the name of the remote source. *<identifier\>* is the name of the table on the remote source.



</dd><dt><b>

*<for\_system\_time\>*

</b></dt>
<dd>

Selects records that were active within the specified validity period. This option is only for use with querying system-versioned tables.

```
<for_system_time> ::= <as_of_spec> | <from_to_spec> | <between_spec>

<as_of_spec> ::= FOR SYSTEM_TIME AS OF '<timestamp1>'
<from_to_spec> ::= FOR SYSTEM_TIME FROM '<timestamp1>' TO '<timestamp2>'
<between_spec> ::= FOR SYSTEM_TIME BETWEEN '<timestamp1>' AND '<timestamp2>'
```

*<as\_of\_spec\>* returns records that were active as of the specified timestamp.

*<from\_to\_spec\>* returns records that were active any time within the specified time range, even if their start time was before *<timestamp1\>* or their end time was after *<timestamp2\>*. Records that stopped being active right at *<timestamp1\>* are not included, nor are records that started being active right at *<timestamp2\>*.

*<between\_spec\>* returns records that were active any time within the specified time range, even if their start time was before *<timestamp1\>* or their end time was after *<timestamp2\>*. But unlike *<from\_to\_spec\>*, it also returns records that started being active right at *<timestamp2\>*.



</dd><dt><b>

*<for\_application\_time\_period\>*

</b></dt>
<dd>

Selects records that were active as of the specified timestamp. This option is only for use with querying application-period time tables.

```
<for_application_time_period> ::= FOR APPLICATION_TIME AS OF '<timestamp>'
```



</dd><dt><b>

*<partition\_restriction\>*

</b></dt>
<dd>

Restricts the query to the specified partition\(s\) of a partitioned table.

```
<partition_restriction> ::= PARTITION ( <partition_number> [ {, <partition_number> }...] )

<partition_number> ::= <unsigned_integer>
```

If no partition is specified, then all partitions are the source of the SELECT. *<partition\_restriction\>* can be obtained from the M\_CS\_PARTITIONS system view. This syntax is available for partitioned tables only.



</dd><dt><b>

*<table\_alias\>*

</b></dt>
<dd>

Specifies an alias for the table or table join.

```
<table_alias> ::= <identifier>
```



</dd><dt><b>

*<tablesample\_clause\>*

</b></dt>
<dd>

Applies the SELECT statement to a random sample of the table data.

```
<tablesample_clause> ::= TABLESAMPLE [ BERNOULLI | SYSTEM ] ( <sample_size> )

<sample_size> ::= <exact_numeric_literal>
```

*<sample\_size\>* specifies the percentage of the table to be returned as a sample.

Values must be greater than 0 and less than or equal to 100. \(100 returns the complete table\). The goal of the TABLESAMPLE operator is to allow queries to be executed over ad-hoc random samples of tables. Samples are computed uniformly over rows in a columnar base table. Samples can either be uniform random samples \(SYSTEM sampling\) or uniform and independent random samples \(BERNOULLI sampling\). SYSTEM sampling exploits the lack of the independence requirement by sampling blocks of rows at a time, while SYSTEM sampling offers performance advantages over BERNOULLI sampling, it comes at the cost of larger variance in sample size.



</dd>
</dl>



</dd><dt><b>

*<subquery\>*

</b></dt>
<dd>

Specifies a SELECT statement as the data source.

```
<subquery> ::= ( <select_statement> )[ [ AS ] <subquery_alias> ] 

<subquery_alias> ::= <identifier>
```

*<subquery\_alias\>* specifies an alias for the subquery.



</dd><dt><b>

*<joined\_table\>*

</b></dt>
<dd>

Specifies a table join.

```
<joined_table> ::= 
 <table_expression> [ <join_type> ] [ <join_cardinality> ] JOIN <table_expression> ON <predicate>
 | <table> CROSS JOIN <table> | <joined_table>
 | <case_join>
```


<dl>
<dt><b>

*<table\>*

</b></dt>
<dd>

Specifies the table to be used in the join.



</dd><dt><b>

*<join\_type\>*

</b></dt>
<dd>

Specifies the join cardinality.

```
<join_type> ::= { INNER | { LEFT | RIGHT | FULL } [ OUTER ] }
```

-   An INNER JOIN returns records that have matching values in both tables.

-   A LEFT \(OUTER\) JOIN returns all records from the left table, and the matched records from the right table

-   A RIGHT \(OUTER\) JOIN returns all records from the right table, and the matched records from the left table

-   A FULL \(OUTER\) JOIN returns all records when there is a match in either left or right table

-   OUTER is an optional keyword that applies to LEFT, RIGHT, and FULL; it does not change the semantics of the join syntax.




</dd><dt><b>

*<join\_cardinality\>*

</b></dt>
<dd>

Specifies the join cardinality.

Join cardinality specifies how many matching entries in one table exist in the other table in a join operation. This information can be exploited for better query performance.

Ensure that you chose the correct join cardinality by validating that the query returns the expected results; imprecise join cardinality can lead to unexpected results.

```
<join_cardinality> ::= { MANY TO MANY
 | MANY TO ONE
 | MANY TO EXACT ONE
 | ONE TO MANY
 | EXACT ONE TO MANY
 | ONE TO ONE
 | EXACT ONE TO ONE
 | ONE TO EXACT ONE
 | EXACT ONE TO EXACT ONE }
```

ONE means 0 or 1 matching record and EXACT ONE means only 1 matching record. MANY means no restriction and it can be 0 record or more than 1 record. If no information is specified, MANY TO MANY is default which means no restriction.



</dd><dt><b>

ON *<predicate\>*

</b></dt>
<dd>

ON *<predicate\>* specifies a join predicate.



</dd><dt><b>

CROSS JOIN

</b></dt>
<dd>

CROSS JOIN is another *<join\_type\>*, but it only allows a *<table\>* on the left and right side, so it is on its own line in the syntax. CROSS JOIN produces the cross-product of two tables. In many SQL dialects, including HANA SQL, a comma is semantically equivalent to the CROSSSELECT \* from table1, table2…CROSS JOIN specifies that a cross join should be performed. However, specifying a comma is not recommended because it has a lower precedence than CROSS JOIN and can return unexpected results, especially when the query also involves outer join operators.



</dd><dt><b>

*<case\_join\>*

</b></dt>
<dd>

Specifies a case join, which allows you to choose a different table to be joined for each record..

```
<case_join> ::= <table_0> LEFT OUTER MANY TO ONE CASE JOIN   
   WHEN <condition_predicate_1> THEN RETURN <output_column_list_1> FROM <table_1> ON <join_predicate_1>
   ...
   WHEN <condition_predicate_N> THEN RETURN <output_column_list_N> FROM <table_N> ON <join_predicate_N>   
  [ ELSE RETURN <output_column_list_N+1> FROM <table_N+1> ON <join_predicate_N+1>]
 END 
```

For each row in *<table\_0\>* , the first satisfied WHEN clause will be joined with the table in the THEN clause.

For the WHEN clause, only columns from left side of a case join can be used

In the THEN clause,*<table\_1\>* represents the joined table name, and *<output\_column\_list\_1\>* represents the projection columns as a result of the join. *<table\_1\>* and *<output\_column\_list\_1\>* must have the same number of columns or an error is returned.

If the WHEN clauses do not produce matches and no ELSE clause is specified, the join produces NULL columns



</dd>
</dl>



</dd><dt><b>

*<lateral\_table\_expression\>*

</b></dt>
<dd>

Allows correlation between table subqueries in the context join operation.

```
<lateral_table_expression> ::= LATERAL ( { <subquery> | <function_reference> } )
```

Lateral joins are only supported for CROSS PRODUCT, INNER JOING and LEFT OUTER JOIN.



</dd><dt><b>

*<collection\_derived\_table\>*

</b></dt>
<dd>

Specifies a collection derived table as the data source.

```
<collection_derived_table> ::= 
 UNNEST ( <collection_value_expression> [ {, <collection_value_expression> }...] ) 
   [ WITH ORDINALITY ] AS <table_alias> [ <derived_column_list> ]

<collection_value_expression> ::= 
 ARRAY ( <table_expression> [ {, <table_expression> }...] | <column_name> )

<derived_column_list> ::= ( <column_name>, ... )
```

Collection-derived tables are similar to lateral tables in that they can contain a reference to another element of the *<from\_clause\>* that has been specified before them. This reference has inner join characteristics because the referenced element of the *<from\_clause\>* is used as a parameter to execute the lateral subquery.

Collection values \(Array\) can be interpreted as the columns of a table by "turning them 90 degrees clockwise".

You can use an array constructor or a field name of ARRAY type.

*<derived\_column\_list\>* specifies a list of column identifiers, ordered in the order of values in the collection value expressions. The column list can be omitted.



</dd><dt><b>

*<function\_reference\>*

</b></dt>
<dd>

Specifies the results of a table function, including SQLScript user-defined table functions, as the data source.

```
<function_reference> ::= <function_name>( <proc_arg_list> | <opt_parameter_key_value_list> )

<function_name> ::= [[<database_name>.]<schema.name>.]<function.identifier>
```

*<proc\_arg\_list\>* and *<opt\_parameter\_key\_value\_list\>* are the allowable arguments and parameters for the function.

*<database\_name\>* and *<schema.name\>* are for use with SQLScript user-defined table functions.

For more information on SQLScript user-defined table functions, see the *SAP HANA Cloud, SAP HANA Database SQLScript*.



</dd><dt><b>

*<table\_variable\>*

</b></dt>
<dd>

Specifies a SQLScript table variable. See the topic on declarative SQLScript logic in *SAP HANA Cloud, SAP HANA Database SQLScript* for more information about table variables.



</dd><dt><b>

*<associated\_table\_expression\>*

</b></dt>
<dd>

Specifies a table that is associated with other tables as the data source.

```
<associated_table_expression> ::=
 <associated_table_name>[ [<condition>]]:<associated_ref>[.<associated_ref>[...] ]
<associated_ref> ::= <column_name>[ [<condition> [ <association_cardinality> ] ] ]

<association_cardinality> ::= USING [ ONE | MANY ] TO { ONE | MANY } JOIN
```

*<condition\>* applies the specified predicate to filter the column values. For example `myTable[myColumn>100]` filters matches values of myColumn that are greater than 100. The square brackets around *<condition\>* are required syntax.

*<association\_cardinality\>* specifies the join to apply.



</dd>
</dl>



</dd><dt><b>

INTO *<variable\_name\_list\>*

</b></dt>
<dd>

Selects values into an array of one or more variables.

```
<variable_name_list> ::= <variable_name> [,<variable_name> [,…] ]

<variable_name> ::= { <identifier> | <identifier> [ <index> ] ] }
```

The bold font used for the square brackets is there to indicate that you specify the square brackets \(for example, `A_COPY[1], B_COPY[1]`.



</dd><dt><b>

*<where\_clause\>*

</b></dt>
<dd>

Specifies predicates on inputs in the FROM clause.

```
<where_clause> ::= WHERE <condition>

<condition> ::= 
 <condition> OR <condition> 
 | <condition> AND <condition>
 | NOT <condition>
 | ( <condition> )
 | <predicate>

   
<predicate> ::= 
 <comparison_predicate>
 | <range_predicate>
 | <in_predicate> 
 | <exist_predicate>
 | <like_predicate> 
 | <null_predicate>
 
<comparison_predicate> ::= 
 <table_expression> { = | != | <> | > | < | >= | <= } [ ANY | SOME | ALL ] ( { <table_expression_list> | <subquery> } )
 
<range_predicate> ::= 
 <table_expression> [ NOT ] BETWEEN <table_expression> AND <table_expression>
 
<in_predicate> ::= 
 <table_expression> [ NOT ] IN ( { <table_expression_list> | <subquery> } )
 
<exist_predicate> ::= 
 [NOT] EXISTS ( <subquery> )
 
<like_predicate> ::= 
 <table_expression> [ NOT ] LIKE <table_expression> [ ESCAPE <table_expression> ]
 
<null_predicate> ::= 
 <table_expression> IS [ NOT ] NULL

<table_expression_list> ::= <table_expression> [, <table_expression> [,… ] ]
```



</dd><dt><b>

*<group\_by\_clause\>*

</b></dt>
<dd>

Groups the selected rows based on the values in the specified columns.

```
<group_by_clause> ::= GROUP BY <group_by_expression_list>

<group_by_expression_list> ::= 
 { <table_expression>|<grouping_set> } [ {, <table_expression>|<grouping_set> } ...]

<grouping_set> ::= 
 { GROUPING SETS | ROLLUP | CUBE }
    [ BEST <signed_integer>]
    [ LIMIT <unsigned_integer> [ OFFSET <unsigned_integer> ] ]
    [ WITH SUBTOTAL ] 
    [ WITH BALANCE ] 
    [ WITH TOTAL ]
    [ STRUCTURED RESULT [ WITH OVERVIEW ] 
    [ PREFIX <prefix_table_name> ] | MULTIPLE RESULTSETS ]
    ( <grouping_expression_list> )

<grouping_expression_list> ::= <grouping_expression> [ {, <grouping_expression> }...]

<grouping_expression> ::= 
 <table_expression> 
 | ( <table_expression> [, <table_expression>...] )
 | ( ( <table_expression> [, <table_expression>...] ) <order_by_clause> )
```


<dl>
<dt><b>

GROUPING SETS

</b></dt>
<dd>

Generates results with specified multiple groupings of data in a single statement. If no additional options are set, such as BEST and LIMIT, then the result produced is the same as a UNION ALL of the aggregation of each specified group.

For example:

```
SELECT col1, col2, col3, * count(*) 
   FROM t 
   GROUP BY GROUPING SETS ( (col1, col2), (col1, col3) );
```

Is equivalent to:

```
SELECT * col1, col2, NULL, count(*) 
   FROM t GROUP BY col1, col2
   UNION ALL
   SELECT col1, NULL, * col3, count(*) 
   FROM t  GROUP BY col1, col3;
```

In the grouping-sets query, each of \(col1, col2\) and \(col1, col3\) specifies the grouping.

If columns are between GROUP BY and grouping sets, then they are common columns of all grouping sets. For example:

```
SELECT col1, col2, col3, * count(*) 
   FROM t 
   GROUP BY col4, col5, GROUPING SETS ( (col1, col2), (col1, col3) );
```

Is equivalent to:

```
SELECT * col1, col2, NULL, count(*) 
   FROM t GROUP BY col4, col5, col1, col2
   UNION ALL
   SELECT col1, NULL, * col3, count(*) 
   FROM t GROUP BYcol4, col5, col1, col3;
```



</dd><dt><b>

ROLLUP

</b></dt>
<dd>

Generates results with multiple levels of aggregation in a single statement.

For example:

```
ROLLUP (col1, col2, col3);
```

Is equivalent to the following statement, with an additional aggregation without grouping.

```
GROUPING SETS ( (col1, col2, col3), (col1, col2), (col1) )
```

Thus, the number of grouping sets that result set contains is the number of columns in ROLLUP list plus one for a last aggregation if there is no additional option.

If columns are between GROUP BY and ROLLUP, then the columns are common columns of all grouping sets. For example:

```
col4, col5, ROLLUP (col1, col2, col3)
```

Is equivalent to:

```
GROUPING SETS ( (col4, col5, col1, col2, col3), (col4, col5, col1, col2), (col4, col5, col1), (col4, col5) )
```



</dd><dt><b>

CUBE

</b></dt>
<dd>

Generates results with multiple levels of aggregations in a single statement.

For example:

```
CUBE (col1, col2, col3)
```

Is equivalent to the following statement, with an additional aggregation without grouping.

```
GROUPING SETS ( (col1, col2, col3), (col1, col2), (col1, col3), (col2, col3), (col1), (col2), (col3) )
```

Thus, the number of grouping sets that result set contains is the same as all possible permutations of columns in the CUBE list plus one for the last aggregation if there is no additional option.

If columns are between GROUP BY and CUBE, then the columns are common columns of all grouping sets. For example:

```
col4, col5, CUBE (col1, col2, col3)
```

is equivalent to:

```
GROUPING SETS( (col4, col5, col1, col2, col3), (col4, col5, col1, col2),
   (col4, col5, col1, col3), (col4, col5, col2, col3), (col4, col5, col1), 
   (col4, col5, col2), (col4, col5, col3), (col4, col5) )
```

Any combination of expression, grouping sets, ROLLUP, and CUBE are possible according to SQL standard. Each of expression, ROLLUP, and CUBE can be converted to a grouping set. Several grouping sets also can be converted to a single grouping set by repeating to combine two successive grouping sets to a single grouping set. Two successive grouping sets are combined to a single grouping set by cross-producing *<grouping\_expression\_list\>*. For example:

```
SELECT col1, col2, col3, * count(*) 
   FROM t GROUP BY GROUPING SETS( (col1, col2), (col3) ), 
   GROUPING SETS( (col4), (col5, col6) );
```

is equivalent to:

```
SELECT col1, col2, col3, * count(*) 
   FROM t GROUP BY GROUPING SETS( (col1, col2, col4), (col3, col4), 
   (col1, col2, col5, col6), (col3, col5, col6 );
```



</dd><dt><b>

BEST *<signed\_integer\>*

</b></dt>
<dd>

Returns only the top-n grouping sets sorted in descending order of the number of rows aggregated in each grouping set.

*<signed\_integer\>* can be zero, positive, and negative. When *<n\>* is zero, it is the same as the BEST option not being set. When *<n\>* is negative, it means sorting in ascending order.

Can be specified for a single column table or a single OLAP view.



</dd><dt><b>

LIMIT

</b></dt>
<dd>

Returns the first *<unsigned\_integer\>* grouped records after skipping OFFSET *<unsigned\_integer\>* for each grouping set.

```
LIMIT <unsigned_integer> [ OFFSET <unsigned_integer> ]
```



</dd><dt><b>

WITH SUBTOTAL

</b></dt>
<dd>

Returns an additional subtotal for each grouping set in the returned results controlled by OFFSET or LIMIT. Unless OFFSET and LIMIT are specified, the value is the same as WITH TOTAL.



</dd><dt><b>

WITH BALANCE

</b></dt>
<dd>

Returns for each grouping set an additional aggregated value of the remaining values not returned by OFFSET or LIMIT.



</dd><dt><b>

WITH TOTAL

</b></dt>
<dd>

Returns for each grouping set an additional row that is the aggregated total value. OFFSET and LIMIT options do not change this value.



</dd><dt><b>

STRUCTURED RESULT

</b></dt>
<dd>

Returns results as temporary tables. For each grouping set a single temporary table is created. If the WITH OVERVIEW option is set, an additional temporary table is created for the overview of the grouping sets. The names of the temporary tables are specified by the PREFIX option.

WITH OVERVIEW Returns an overview in a separate additional table.



</dd><dt><b>

PREFIX

</b></dt>
<dd>

Specifies a prefix for naming the temporary tables.

```
PREFIX <prefix_table_name>

<prefix_table_name> ::= #<identifier>
```

*<prefix\_table\_name\>* must start with "\#", which means a temporary table. If PREFIX is not specified, the default prefix is "\#GN" followed by a non-negative integer number. See [Return Format](select-statement-for-sap-hana-database-68b8472.md#loio68b84729d44b4e2cbc4b4b851193995d__Return_Format).



</dd><dt><b>

MULTIPLE RESULTSETS

</b></dt>
<dd>

Specifies that results should be returned in multiple result sets.



</dd>
</dl>

Related Functions:

-   GROUPING\_ID\(column\_name\_list\) function returns an integer number to identify which grouping set each grouped record belongs to.

-   GROUPING\(column\) function returns 1 if the column is used for grouping. Otherwise it returns 0.


Return Format:

-   If neither STRUCTURED RESULT nor MULTIPLE RESULTSETS is set, then the union result of all grouping sets is returned with NULL values filling up attributes that are not included in a specific grouping set.

-   With STRUCTURED RESULT, temporary tables are created additionally, and can be queried using "SELECT \* FROM *<table\_name\>*" in the same session. The name of the tables follows the form:

    -   *<PREFIX\>*0: this table contains the overview if WITH OVERVIEW is specified

    -   *<PREFIX\>*n: n-th grouping set subject to re-ordering by the BEST parameter


-   With MULTIPLE RESULTSETS, multiple result sets are returned. Grouped records for each grouping set are in a single result set.




</dd><dt><b>

*<having\_clause\>*

</b></dt>
<dd>

Selects the specified groups that satisfy the predicates.

```
<having_clause> ::= HAVING <condition>
```

If this clause is omitted, all groups are selected.



</dd><dt><b>

*<set\_operator\>*

</b></dt>
<dd>

Enables multiple SELECT statements to be combined but return only one result set.

```
<set_operator> ::= 
 UNION [ ALL | DISTINCT ] 
 | INTERSECT [ DISTINCT ] 
 | EXCEPT [ DISTINCT ]
```


<dl>
<dt><b>

UNION ALL

</b></dt>
<dd>

Selects all records from all SELECT statements. Duplicates are not removed.



</dd>
</dl>


<dl>
<dt><b>

UNION \[DISTINCT\]

</b></dt>
<dd>

Selects all unique records from all SELECT statements by removing duplicates found from different SELECT statements. UNION has the same function as UNION DISTINCT.



</dd>
</dl>


<dl>
<dt><b>

INTERSECT \[DISTINCT\]

</b></dt>
<dd>

Returns records that exist in all SELECT statement results.



</dd>
</dl>


<dl>
<dt><b>

EXCEPT \[DISTINCT\]

</b></dt>
<dd>

Returns all unique records from the first SELECT statements after removing the duplicates in the following SELECT statements. MINUS is accepted as a synonym for EXCEPT.



</dd>
</dl>



</dd><dt><b>

*<order\_by\_clause\>*

</b></dt>
<dd>

Sorts records by expressions \(such as columns\) or by positions.

```
<order_by_clause> ::= 
 ORDER BY { <order_by_expression> [, order_by_expression [,…] ] }

<order_by_expression> ::= 
 <table_expression> [ <collate_clause> ] [ ASC | DESC ] [ NULLS FIRST | NULLS LAST ] 
 | <position> [ <collate_clause> ] [ ASC | DESC ] [ NULLS FIRST | NULLS LAST ] 
<position> ::= <unsigned_integer>

<collate_clause> ::= COLLATE <collation_name>
```


<dl>
<dt><b>

*<collate\_clause\>*

</b></dt>
<dd>

Specifies the collation to use. *<collate\_clause\>* can only be used on columns defined as NVARCHAR or VARCHAR.

*<collation\_name\>* is one of the supported collation names listed in the COLLATIONS system view.



</dd><dt><b>

\[ ASC | DESC \]

</b></dt>
<dd>

ASC sorts records in ascending order and DESC sorts records in descending order. The default is ASC.



</dd><dt><b>

\[ NULLS FIRST | NULLS LAST \]

</b></dt>
<dd>

Specifies the ordering of NULL values.



</dd><dt><b>

*<position\>*

</b></dt>
<dd>

*<position\>* uses the entries in the select list to define the ordering required. For example:

```
SELECT col1, col2 FROM t ORDER BY 2;
```

ORDER BY 2 indicates that ordering should be undertaken using the second expression in the select list, which in this case is col2.



</dd>
</dl>



</dd><dt><b>

*<limit\_clause\>*

</b></dt>
<dd>

Limits the number of records returned and behaves like TOP.

```
<limit_clause> ::= 
 LIMIT <unsigned_integer> [ OFFSET <unsigned_integer> ] [ TOTAL ROWCOUNT ]
```

Specify TOTAL ROWCOUNT to update the session variable TOTAL\_ROWCOUNT with the total number of rows the query would return if not limited. You can then query the value of the TOTAL\_ROWCOUNT session variable \(for example,`SELECT SESSION_CONTEXT('TOTAL_ROWCOUNT') FROM DUMMY;`\).



</dd>
</dl>



<a name="loio68b84729d44b4e2cbc4b4b851193995d__section_fgs_cqs_pz"/>

## Description

SELECT statements can be nested inside of statements such as another SELECT statement or an INSERT INTO or UPDATE statement. A SELECT statement that is nested in another statement is called a **subquery**. A subquery acts as a sort of filter, returning a set of data to the main statement that has some condition applied. For example, in the statement <code>SELECT last_name FROM Students WHERE student_id IN (<b>SELECT student_id FROM Class_Registration</b>)</code>, the SELECT statement that is inside of the parenthesis is a subquery.

The subquery queries the Student\_Registration table and returns \(only\) the IDs of students who have registered for a class. The outer, main query then queries the Students table for the last names that correspond with the student\_ids retrieved from the Class\_Registration table \(this simplistic example presumes there’s a student\_ID column in both tables\).



<a name="loio68b84729d44b4e2cbc4b4b851193995d__section_lvd_dqq_ybb"/>

## Privileges

You must have SELECT privileges on the object you’re querying.

To query a system-versioned table, you must have the SELECT privilege on the table and on its associated history table.



<a name="loio68b84729d44b4e2cbc4b4b851193995d__sql_select_1sql_select_example"/>

## Examples


<dl>
<dt><b>

Examples with WAIT and NOWAIT

</b></dt>
<dd>

```
CREATE COLUMN TABLE x ( a INT, b INT );
INSERT INTO x VALUES (1,1);
INSERT INTO x VALUES (2,2);
CREATE COLUMN TABLE y ( a INT, b INT );
INSERT INTO y VALUES (1,1);
INSERT INTO y VALUES (2,2);
SELECT * FROM x WHERE a=1 FOR UPDATE WAIT 1; --> OK
SELECT * FROM y WHERE b=1 FOR UPDATE NOWAIT; --> OK
COMMIT;
SELECT * FROM x WHERE a=1 FOR UPDATE OF x.c; --> error because c column does not exist in table x.
SELECT * FROM x WHERE a=1 FOR UPDATE OF x.a; --> OK
COMMIT;
SELECT * FROM x, y WHERE a=1 FOR UPDATE; --> error because "OF" is not used to specify which one of x and y is locked.
SELECT * FROM x, y WHERE a=1 FOR UPDATE OF y.b; --> OK
COMMIT;
SELECT * FROM x, (SELECT * FROM y) WHERE a=1 FOR UPDATE OF y.b;  --> error because y is inside subquery
COMMIT;
```



</dd><dt><b>

Examples with WITH

</b></dt>
<dd>

```
CREATE TABLE t1(a INT, b INT);
 WITH q1 AS (SELECT * FROM t1) SELECT * FROM q1;
 WITH q1(c1, c2) AS (SELECT * FROM t1) SELECT * FROM q1;
 WITH q1(c1) AS (SELECT a+b FROM t1), q2(c2) AS (SELECT MAX(c1) FROM q1) SELECT c1 FROM q1 UNION ALL SELECT c2 FROM q2;
```



</dd><dt><b>

Example with FOR XML

</b></dt>
<dd>

The following fictitious example shows what the results could look like when specifying FOR XML with the schemaloc, targetns, and nullstyle options:

```
SELECT C1, C2 FROM T1
 FOR XML ('schemaloc'='http://thiscompany.com/schemalib', 'targetns'='http://thiscompany.com/samples', 'nullstyle'='omit');
```


<table>
<tr>
<th valign="top">



</th>
</tr>
<tr>
<td valign="top">

```
<resultset schemalocation="http://thiscompany.com/schemalib" targetnamespace="http://thiscompany.com/samples">
   <row>
      <C1>1</C1>
      <C2>a</C2>
   </row>
   <row>
      <C1>11</C1>
      <C2>ab</C2>
   </row>
   <row>
      <C1>11c</C1>
   </row>
</resultset>

```



</td>
</tr>
</table>



</dd><dt><b>

Examples with GROUP BY GROUPING SETS

</b></dt>
<dd>

Create a column table, t1, and populate it with some example data.

```
CREATE COLUMN TABLE t1 ( id INT PRIMARY KEY, customer VARCHAR(5), year INT, product VARCHAR(5), sales INT );
 INSERT INTO t1 VALUES(1, 'C1', 2009, 'P1', 100);
 INSERT INTO t1 VALUES(2, 'C1', 2009, 'P2', 200);
 INSERT INTO t1 VALUES(3, 'C1', 2010, 'P1', 50);
 INSERT INTO t1 VALUES(4, 'C1', 2010, 'P2', 150);
 INSERT INTO t1 VALUES(5, 'C2', 2009, 'P1', 200);
 INSERT INTO t1 VALUES(6, 'C2', 2009, 'P2', 300);
 INSERT INTO t1 VALUES(7, 'C2', 2010, 'P1', 100);
 INSERT INTO t1 VALUES(8, 'C2', 2010, 'P2', 150);
```

Use grouping sets to analyze the customer data.

```
SELECT customer, year, product, SUM(sales)
     FROM t1
     GROUP BY GROUPING SETS
     (
      (customer, year),
      (customer, product)
     );

 SELECT customer, year, NULL, SUM(sales)
     FROM t1
     GROUP BY customer, year
 UNION ALL
 SELECT customer, NULL, product, SUM(sales)
     FROM t1
     GROUP BY customer, product;
```

Observe that the two groups inside grouping sets in the first query are specified in each GROUP BY clause in the second query.

Use ROLLUP to generate results with multiple levels of aggregation:

```
SELECT customer, year, SUM(sales)
     FROM t1
     GROUP BY ROLLUP(customer, year);

 SELECT customer, year, SUM(sales)
     FROM t1
     GROUP BY GROUPING SETS
     (
      (customer, year),
      (customer)
     )
 UNION ALL
 SELECT NULL, NULL, SUM(sales)
     FROM t1; 
```

Use CUBE to generate results with multiple levels of aggregation.

```
SELECT customer, year, SUM(sales)
     FROM t1
     GROUP BY CUBE(customer, year);

 SELECT customer, year, SUM(sales)
     FROM t1
     GROUP BY GROUPING SETS
     (
      (customer, year),
      (customer),
      (year)
     )
 UNION ALL
 SELECT NULL, NULL, SUM(sales)
     FROM t1;
```

Use BEST 1 to return only the best group of results.

```
SELECT customer, year, product, SUM(sales)
     FROM t1
     GROUP BY GROUPING SETS BEST 1
     (
      (customer, year),
      (product)
     );
```

Use LIMIT 2 to limit the number of records to a maximum 2 for each group.

```
SELECT customer, year, product, SUM(sales)
     FROM t1
     GROUP BY GROUPING SETS LIMIT 2
     (
      (customer, year),
      (product)
     );
```

For the \(customer, year\) group, the number of records are 4, so only first 2 records are returned. For the \(product\) group, the number of records are 2, so all the records are returned.

Use WITH SUBTOTAL to produce an additional record for each group that displays a subtotal of returned records. These subtotal records are NULL for the customer, year, product columns, and the sum of sum\(sales\) values in the select list.

```
SELECT customer, year, product, SUM(sales)
     FROM t1
     GROUP BY GROUPING SETS LIMIT 2 WITH SUBTOTAL
     (
      (customer, year),
      (product)
     );
```

Use WITH BALANCE to produce an additional record for each group that displays a subtotal of unreturned records.

```
SELECT customer, year, product, SUM(sales)
     FROM t1
     GROUP BY GROUPING SETS LIMIT 2 WITH BALANCE
     (
      (customer, year),
      (product)
     );
```

Use WITH TOTAL to produce an additional record for each group that displays a total of all grouped records.

```
SELECT customer, year, product, SUM(sales)
     FROM t1
     GROUP BY GROUPING SETS LIMIT 2 WITH TOTAL
     (
      (customer, year),
      (product)
     );
```

Use STRUCTURED RESULT to create temporary tables, one for each grouping set and an additional table for the overview table.

```
SELECT customer, year, product, SUM(sales)
     FROM t1
     GROUP BY GROUPING SETS STRUCTURED RESULT
     (
      (customer, year),
      (product)
     );

 SELECT * FROM "#GN1";
 SELECT * FROM "#GN2";
```

"\#GN1" table is for \(customer, year\) grouping set and "\#GN2" table is for \(product\) one.

Each table contains only related columns. So, "\#GN1" table doesn’t have "product" column and "\#GN2" table doesn’t have "customer" and "year" columns.

Use WITH OVERVIEW to create a temporary table "\#GN0" for the overview table.

```
DROP TABLE "#G1";
 DROP TABLE "#G2";

 SELECT customer, year, product, SUM(sales)
     FROM t1
     GROUP BY GROUPING SETS STRUCTURED RESULT WITH OVERVIEW
     (
      (customer, year),
      (product)
     );

 SELECT * FROM "#GN0";
 SELECT * FROM "#GN1";
 SELECT * FROM "#GN2";
```

Change the names of temporary tables by using the PREFIX keyword.

The names of tables must start with '\#', which is the prefix used for temporary tables.

```
SELECT customer, year, product, SUM(sales)
     FROM t1
     GROUP BY GROUPING SETS STRUCTURED RESULT WITH OVERVIEW PREFIX '#MYTAB'
     (
      (customer, year),
      (product)
     );

 SELECT * FROM "#MYTAB0";
 SELECT * FROM "#MYTAB1";
 SELECT * FROM "#MYTAB2";
```

Temporary tables are dropped when the corresponding session is closed or when a user executes a drop command. A list of temporary tables is seen in m\_temporary\_tables.

```
SELECT * FROM m_temporary_tables;
```

Use MULTIPLE RESULTSETS to return multiple result sets. The following query returns three result sets, one for the overview table and two for the grouping sets.

```
SELECT customer, year, product, SUM(sales)
     FROM t1
     GROUP BY GROUPING SETS MULTIPLE RESULTSETS
     (
      (customer, year),
      (product)
     );
```



</dd><dt><b>

Example with TABLESAMPLE

</b></dt>
<dd>

Use TABLESAMPLE to select a random sample of 1% of the employee table and within that sample count the number of managers.

```
SELECT COUNT(*), AVG(salary)
    FROM employee TABLESAMPLE SYSTEM (1)
    WHERE employee.type = 'manager';
```



</dd><dt><b>

Examples with EXPRESSION MACROS

</b></dt>
<dd>

The following example creates a view with an expression macro, avgA, and then selects from that view.

```
CREATE TABLE t1(a INT);
INSERT INTO t1 VALUES(10);
INSERT INTO t1 VALUES(20);
CREATE VIEW v1 AS SELECT * FROM t1 WITH EXPRESSION MACROS(AVG(a) AS avgA);
SELECT EXPRESSION_MACRO(avgA) FROM v1;
```



</dd>
<dd>

The following example creates a view, v1, with expression macros, sum\_x and count\_y:

```
CREATE TABLE t (x INT, y INT);
INSERT INTO t VALUES(1, 1);
INSERT INTO t VALUES(2, 1);
INSERT INTO t VALUES(3, 1);
INSERT INTO t VALUES(4, 1);
            
CREATE VIEW V1 AS SELECT * FROM t WITH EXPRESSION MACROS (
    SUM(x) AS sum_x,
    COUNT(y) AS count_y
  );
```

The following statements create another view, v2, that uses expression macros from the first view and gives them the new aliases, sum\_x2 and count\_y2.

```
CREATE VIEW v2 AS SELECT * FROM v1 WITH EXPRESSION MACROS (
    sum_x AS sum_x2,
    count_y AS count_y2
  );
```

The following statement selects the expression macro values from v2. The final SELECT statement returns `10, 4`.

```
SELECT EXPRESSION_MACRO(sum_x2), EXPRESSION_MACRO(count_y2) FROM v2;
```



</dd><dt><b>

Example with HINTS

</b></dt>
<dd>

In the following example, the USE\_OLAP\_PLAN hint is applied.

```
SELECT T2.* FROM ( SELECT MAX(COL) FROM T1 GROUP BY COL WITH HINT( NO_USE_OLAP_PLAN )) T2 WITH HINT( USE_OLAP_PLAN );
```

In the following example, no hint is applied.

```
SELECT T2.* FROM ( SELECT MAX(COL) FROM T1 GROUP BY COL WITH HINT( NO_USE_OLAP_PLAN )) T2;
```

Examples for cache controlling hints:

```
SELECT FROM T1 WITH HINT( IGNORE_PLAN_CACHE ); 
SELECT FROM T1 WITH HINT( USE_REMOTE_CACHE );
```

Examples for execution engine selection with hints:

```
SELECT FROM T1 WITH HINT( USE_OLAP_PLAN ); 
SELECT FROM T1 WITH HINT( NO_USE_OLAP_PLAN );
```

Examples for controlling the access path with hints:

```
SELECT FROM T1 WITH HINT( INDEX_SEARCH ); 
SELECT FROM T1 WITH HINT( NO_INDEX_SEARCH );
```

Examples for controlling join operations with hints:

```
SELECT FROM T1, T2 WITH HINT( INDEX_JOIN ); 
SELECT FROM T1, T2 WITH HINT( NO_INDEX_JOIN ); 
SELECT FROM T1, T2 WITH HINT( HASH_JOIN ); 
SELECT FROM T1, T2 WITH HINT( NO_HASH_JOIN ); 
SELECT FROM T1, T2 WITH HINT( MIXED_INVERTED_INDEX_JOIN ); 
SELECT FROM T1, T2 WITH HINT( NO_MIXED_INVERTED_INDEX_JOIN );
SELECT FROM T1, T2 WITH HINT( NO_OPTIMIZE_METAMODEL );
```

Examples for query rewriting and logical transformations with hints:

```
SELECT FROM T1 WITH HINT( SUBPLAN_SHARING); 
SELECT FROM T1 WITH HINT( NO_SUBPLAN_SHARING );
```



</dd><dt><b>

Examples of selecting from arrays

</b></dt>
<dd>

Select values from the array column C1 in table T1.

```
SELECT C1 FROM T1;
```

Select an array value using array construction by enumeration.

```
SELECT ARRAY ( 1, 2, 3, 4 ) FROM DUMMY;
```

Select an array value using array construction by query.

```
SELECT ARRAY( SELECT C1 FROM T0 ) FROM DUMMY;
```



</dd><dt><b>

Example with PARTITION

</b></dt>
<dd>

You use PARTITION to select the data contained in partitions 1, 3 and 4 of table `T0`.

```
SELECT * FROM T0 PARTITION (1, 3, 4);
```



</dd><dt><b>

Example with FOR SHARE LOCK

</b></dt>
<dd>

This example involves 3 sessions and all of them are in auto-commit-off mode and read-committed isolation level:

```
--in Session 1: 
CREATE TABLE X (A INT);
INSERT INTO X VALUES (0);
COMMIT;

-- in session 2:
SELECT A FROM X FOR SHARE LOCK;    -- OK, {0} returned

-- in session 3:
SELECT A FROM X FOR SHARE LOCK;    -- OK, {0} returned. Now, record 0 has two shared-lock owners: session 2 and Session 3

-- in session 1:
SELECT A FROM X;                   –- OK, {0} returned; read access is allowed
UPDATE X SET A = 1;                -- lock wait
```

In the previous example, the UPDATE statement tries to acquire exclusive-lock on record 0. If session 1 and session 3 issue either a COMMIT or a ROLLBACK before session 1’s lock timeout is reached, then session 1 successfully updates the record. If session 2 or session 3 holds the lock longer than session 1’s lock timeout, then session 1 gets a lock timeout error and will be rolled back.

The next example involves two sessions, both of which are in auto-commit-off mode and read-committed isolation level, and show how FOR SHARE LOCK guarantees that there are no on-going writers on the queried records.

```
--session 1:
CREATE TABLE X (A INT);
INSERT INTO X VALUES (0);
COMMIT;
UPDATE X SET A = 1;               -- OK, updated records = 1

--session 2:
SELECT A FROM X FOR SHARE LOCK;   -- lock wait, since session 1 is holding exclusive lock on record 0 (for a maximum of session 2’s lock timeout value)

--session 1:
COMMIT;                           –- now that session 1 has executed a COMMIT statement, session 2 can proceed and a 1 is returned. 
```

Note that session 1 is in read-committed isolation level; thus, the updated record is returned after waiting for the record lock.



</dd><dt><b>

Examples with ASSOCIATIONS

</b></dt>
<dd>

The following statements create three tables, and populate them with data:

```
CREATE ROW TABLE EMPLOYEES (ID INT, NAME VARCHAR(20), CITY_ID INT) WITH ASSOCIATIONS (JOIN CITIES AS CITY ON CITY.ID = CITY_ID);
CREATE ROW TABLE CITIES (ID INT, NAME VARCHAR(20), STATE_ID INT) WITH ASSOCIATIONS (JOIN STATES AS STATE ON STATE.ID = STATE_ID);
CREATE ROW TABLE STATES (ID INT, NAME VARCHAR(20));

INSERT INTO STATES VALUES(1, 'California');
INSERT INTO STATES VALUES(2, 'Washington');

INSERT INTO CITIES VALUES(1, 'San Francisco', 1);
INSERT INTO CITIES VALUES(2, 'Los Angeles', 1);
INSERT INTO CITIES VALUES(3, 'Oakland', 1);

INSERT INTO EMPLOYEES VALUES(1, 'Tom', 1);
INSERT INTO EMPLOYEES VALUES(2, 'Jerry', 2);
INSERT INTO EMPLOYEES VALUES(3, 'Mick', 1);
INSERT INTO EMPLOYEES VALUES(4, 'Steve', 3);
```

The following statement queries the EMPLOYEES table using the association with the CITIES table:

```
SELECT * FROM EMPLOYEES:CITY.STATE;
```


<table>
<tr>
<th valign="top">

ID



</th>
<th valign="top">

Name



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

California



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

Washington



</td>
</tr>
</table>

The following statement filters values in the ID columns of the EMPLOYEES and CITIES tables in the query:

```
SELECT * FROM EMPLOYEES[ID<5]:CITY.STATE[ID<2];
```


<table>
<tr>
<th valign="top">

ID



</th>
<th valign="top">

Name



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

California



</td>
</tr>
</table>



</dd><dt><b>

Example with CASE JOIN

</b></dt>
<dd>

The following example shows how to use a CASE JOIN to choose a different table to be joined for each record that matches:

```
CREATE COLUMN TABLE t1 (branch INT, id INT, c1 INT, c2 INT);
CREATE COLUMN TABLE t2 (id INT, c1 INT, c2 INT);
CREATE COLUMN TABLE t3 (id INT, c1 INT, c2 INT);
            
INSERT INTO t1 VALUES (1, 1, 100, 200);
INSERT INTO t1 VALUES (2, 1, 10, 20);
INSERT INTO t2 VALUES (1, 100, 200);
INSERT INTO t3 VALUES (1, 300, 400);
            
SELECT t1.branch, case_join.c1, case_join.c2
   FROM t1 LEFT OUTER MANY TO ONE CASE JOIN
      WHEN t1.branch = 1 THEN RETURN (c1, c2) FROM t2 ON t1.id = t2.id
      WHEN t1.branch = 2 THEN RETURN (c1, c2) FROM t3 ON t1.id = t3.id
     END AS case_join;
```


<table>
<tr>
<th valign="top">

Branch



</th>
<th valign="top">

C1



</th>
<th valign="top">

C2



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

100



</td>
<td valign="top">

200



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

300



</td>
<td valign="top">

400



</td>
</tr>
</table>



</dd><dt><b>

Example of LATERAL JOIN

</b></dt>
<dd>

This example shows how to use a LATERAL join where table TB references columns from table TA.

```
SELECT TA.a1, TB.b1 FROM TA, LATERAL (SELECT b1, b2 FROM TB WHERE b3 = TA.a3) TB WHERE TA.a2 = TB.b2;
```



</dd><dt><b>

Example using TOTAL\_ROWCOUNT to determine total number of rows that would be returned

</b></dt>
<dd>

The following example shows how to use the TOTAL\_ROWCOUNT session variable with LIMIT to determine the number of rows a query would return, without having to fetch all of the rows:

```
CREATE COLUMN TABLE test_rowcount(a INT, b INT);
INSERT INTO test_rowcount VALUES (1,1);
INSERT INTO test_rowcount VALUES (2,2);
INSERT INTO test_rowcount VALUES (3,3);

SELECT * FROM test_rowcount LIMIT 1 TOTAL ROWCOUNT; <-- TOTAL_ROWCOUNT session variable is updated to 3

SELECT SESSION_CONTEXT('TOTAL_ROWCOUNT') FROM DUMMY; <-- Returns the value of the session variable (3)
```



</dd>
</dl>

**Related Information**  


[SAP HANA Cloud, SAP HANA Database SQLScript](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2021_01_QRC/en-US)

