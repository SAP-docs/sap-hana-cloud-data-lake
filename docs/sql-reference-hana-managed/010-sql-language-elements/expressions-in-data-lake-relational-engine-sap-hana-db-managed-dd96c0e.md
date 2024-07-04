<!-- loiodd96c0e0259f40d0a94adce7ab6dd73c -->

# Expressions in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Expressions are formed from different kinds of elements, such as constants, column names, SQL operators, and subqueries.



```
expression:
<case-expression>
| <constant>
| [ <correlation-name>. ] <column-name >
| - <expression>
| <expression operator> <expression>
| ( <expression> )
| <function-name> ( <expression>, … )
| <if-expression>
| ( <subquery> )
| <variable-name>
```

```
<case-expression> ::=
{ CASE <search-condition>
... WHEN <expression> THEN <expression> [ , … ]
... [ ELSE <expression> ] 
END
| CASE
... WHEN <search-condition> THEN <expression> [ , … ]
... [ ELSE <expression> ] 
END }
```

```
<constant> ::=
{ <integer> | <number> | '<string>'
 | <special-constant> | <host-variable> }
```

```
<special-constant> ::=
{ CURRENT { DATE | TIME | TIMESTAMP | USER }
| LAST USER
| NULL
| SQLCODE
| SQLSTATE }
```

```
<if-expression> ::=
IF <condition>
... THEN <expression>
... [ ELSE <expression> ]
ENDIF
```

```
<operator> ::=
{ + | - | * | / | || | % }
```



<a name="loiodd96c0e0259f40d0a94adce7ab6dd73c__iq_refbb_47"/>

## Authorization

You are connected to the database.



<a name="loiodd96c0e0259f40d0a94adce7ab6dd73c__iq_refbb_48"/>

## Side Effects

None.

**Related Information**  


[SQL Operators in Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a4f0a69e84f21015a193d1e9a02d4210.html "These topics describe the arithmetic, string, and bitwise operators available in data lake Relational Engine.") :arrow_upper_right:

[Subqueries in Search Conditions](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a4fb435084f2101592cffd5b502c42fb.html "A subquery is a SELECT statement enclosed in parentheses. Such a SELECT statement must contain one and only one select list item.") :arrow_upper_right:

[Special Values in Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a506ddee84f210158450cf0eaa071698.html "Special values can be used in expressions, and as column defaults when creating tables.") :arrow_upper_right:

[Comparison Conditions](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a4fabf2584f21015a9d8c032cbfdc9a7.html "Comparison conditions in search conditions use a comparison operator.") :arrow_upper_right:

[NULL Value in Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a5107a2e84f2101595bd9bacac97b5be.html "Use NULL to specify a value that is unknown, missing, or not applicable.") :arrow_upper_right:

[Search Conditions in Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a4fa3d9e84f21015a4a6a9424156ed9e.html "Conditions are used to choose a subset of the rows from a table, or in a control statement such as an IF statement to determine control of flow.") :arrow_upper_right:

[Strings in Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a4ed4ede84f21015a8499167b3f9d18a.html "Strings are either literal strings, or expressions with CHAR or VARCHAR data types.") :arrow_upper_right:

[Three-Valued Logic](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a501bc6584f21015a0cfba5d035e295b.html "The AND, OR, NOT, and IS logical operators of SQL work in three-valued logic.") :arrow_upper_right:

