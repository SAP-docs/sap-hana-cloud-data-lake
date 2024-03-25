<!-- loioa4ed4ede84f21015a8499167b3f9d18a -->

# Strings in Data Lake Relational Engine

Strings are either literal strings, or expressions with CHAR or VARCHAR data types.



A literal string is any sequence of characters enclosed in apostrophes \('single quotes'\). A SQL variable of character data type can hold a string. This is a simple example of a literal string:

```
'This is a string.'
```

An expression with a `CHAR` data type might be a built-in or user-defined function, or one of the many other kinds of expressions available.



<a name="loioa4ed4ede84f21015a8499167b3f9d18a__strings_section2"/>

## Special Characters in Strings

Represent special characters in strings by escape sequences, as follows:

-   To represent an apostrophe inside a string, use two apostrophes \(`''`\) in a row. For example:

    ```
    'John''s database'
    ```

-   To represent a newline character, use a backslash followed by n \(`\n`\). For example:

    ```
    'First line:\nSecond line:'
    ```

-   To represent a backslash character, use two backslashes in a row \(`\\`\). For example:

    ```
    'c:\\temp'
    ```

-   Hexadecimal escape sequences can be used for any character, printable or not. A hexadecimal escape sequence is a backslash followed by an x followed by two hexadecimal digits \(for example, \\x6d represents the letter m\). For example:

    ```
    '\x00\x01\x02\x03'
    ```




<a name="loioa4ed4ede84f21015a8499167b3f9d18a__strings_section3"/>

## Compatibility

For compatibility with SAP Adaptive Server Enterprise, you can set the `QUOTED_IDENTIFIER` database option to OFF. With this setting, you can also use double quotes to mark the beginning and end of strings. The option is ON by default.

**Related Information**  


[SQL Operators in Data Lake Relational Engine](sql-operators-in-data-lake-relational-engine-a4f0a69.md "These topics describe the arithmetic, string, and bitwise operators available in data lake Relational Engine.")

[Subqueries in Search Conditions](subqueries-in-search-conditions-a4fb435.md "A subquery is a SELECT statement enclosed in parentheses. Such a SELECT statement must contain one and only one select list item.")

[Comparison Conditions](comparison-conditions-a4fabf2.md "Comparison conditions in search conditions use a comparison operator.")

[Expressions in Data Lake Relational Engine](expressions-in-data-lake-relational-engine-a4ee102.md "Expressions are formed from different kinds of elements, such as constants, column names, SQL operators, and subqueries.")

[NULL Value in Data Lake Relational Engine](null-value-in-data-lake-relational-engine-a5107a2.md "Use NULL to specify a value that is unknown, missing, or not applicable.")

[Search Conditions in Data Lake Relational Engine](search-conditions-in-data-lake-relational-engine-a4fa3d9.md "Conditions are used to choose a subset of the rows from a table, or in a control statement such as an IF statement to determine control of flow.")

[Three-Valued Logic](three-valued-logic-a501bc6.md "The AND, OR, NOT, and IS logical operators of SQL work in three-valued logic.")

[Strings in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/b5f28c46b0ba4ba1915249c2ad0cf44a.html "Strings are either literal strings, or expressions with CHAR or VARCHAR data types.") :arrow_upper_right:

