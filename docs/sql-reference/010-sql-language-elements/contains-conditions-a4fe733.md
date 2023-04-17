<!-- loioa4fe733c84f21015b55d8a431cf44419 -->

# CONTAINS Conditions

Use CONTAINS conditions in subqueries to define text-matching.



The syntax for CONTAINS conditions for a column with a WD index is as follows:

```
{ <column-name> [ NOT ] CONTAINS ( ( <word1> [ , <word2> ] [ , <word3> ] … )
```

The *<column-name\>* must be a `CHAR`, `VARCHAR`, or `LONG VARCHAR` \(`CLOB`\) column in a base table, and must have a WD index. The *<word1\>*, *<word2\>*, and *<word3\>* expressions must be string constants no longer than 255 bytes, each containing exactly one word. The length of that word cannot exceed the maximum permitted word length of the word index of the column.

Without the NOT keyword, the CONTAINS condition is TRUE if *<column-name\>* contains each of the words, UNKNOWN if *<column-name\>* is the NULL value, and FALSE otherwise. The NOT keyword reverses these values but leaves UNKNOWN unchanged.

For example, the following search condition is TRUE if the value of *<varchar\_col\>* is `The cat is on the mat`:

```
varchar_col CONTAINS ('cat', 'mat')
```

This condition is FALSE, however, if the value of *<varchar\_col\>* is `The cat chased the mouse`.

When data lake Relational Engine executes a statement containing both LIKE and CONTAINS, the CONTAINS condition takes precedence.

Avoid using the CONTAINS predicate in a view that has a user-defined function, because the CONTAINS criteria are ignored. Use the LIKE predicate with wildcards instead, or issue the query outside of a view.

