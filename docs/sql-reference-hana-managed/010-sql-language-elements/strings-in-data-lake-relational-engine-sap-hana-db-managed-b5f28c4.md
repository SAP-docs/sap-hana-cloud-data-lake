<!-- loiob5f28c46b0ba4ba1915249c2ad0cf44a -->

# Strings in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Strings are either literal strings, or expressions with CHAR or VARCHAR data types.



A literal string is any sequence of characters enclosed in apostrophes \('single quotes'\). A SQL variable of character data type can hold a string. This is a simple example of a literal string:

```
'This is a string.'
```

An expression with a `CHAR` data type might be a built-in or user-defined function, or one of the many other kinds of expressions available.



<a name="loiob5f28c46b0ba4ba1915249c2ad0cf44a__section_ewb_xs2_bwb"/>

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




<a name="loiob5f28c46b0ba4ba1915249c2ad0cf44a__section_a3w_xs2_bwb"/>

## Compatibility

For compatibility with SAP Adaptive Server Enterprise, you can set the `QUOTED_IDENTIFIER` database option to OFF. With this setting, you can also use double quotes to mark the beginning and end of strings. The option is ON by default.

**Related Information**  


[Strings in Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a4ed4ede84f21015a8499167b3f9d18a.html "Strings are either literal strings, or expressions with CHAR or VARCHAR data types.") :arrow_upper_right:

