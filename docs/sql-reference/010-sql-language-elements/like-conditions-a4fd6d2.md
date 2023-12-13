<!-- loioa4fd6d2984f21015a71d97606b86f4f2 -->

# LIKE Conditions

Use LIKE conditions in subqueries to use wildcards in the WHERE clause to perform pattern matching.



The syntax for LIKE conditions is:

```
<expression> [ NOT ] LIKE <pattern> [ ESCAPE <escape-expr> ]
```

The LIKE condition can evaluate as TRUE, FALSE, or UNKNOWN. You can use LIKE only on string data.

You cannot use subqueries inside a LIKE predicate.

LIKE predicates that start with characters other than wildcard characters may execute faster if an HG index is available.

Certain LIKE predicates execute faster, if either of the following conditions is true:

-   A WD index is available, provided the LIKE pattern contains at least one word bounded on the left end by whitespace or the end of the pattern
-   An NGRAM TEXT index is available, provided the LIKE pattern contains at least *<N\>* contiguous nonwildcard characters

Without the NOT keyword, the condition evaluates as TRUE if *<expression\>* matches the *<pattern\>*. If either *<expression\>* or *<pattern\>* is the NULL value, then this condition is UNKNOWN. The NOT keyword reverses the meaning of the condition but leaves UNKNOWN unchanged.

The pattern might contain any number of wildcard characters. The wildcard characters are:


<table>
<tr>
<th valign="top">

Wildcard

</th>
<th valign="top">

Matches

</th>
</tr>
<tr>
<td valign="top">

\_ \(underscore\)

</td>
<td valign="top">

Any one character

</td>
</tr>
<tr>
<td valign="top">

% \(percent\)

</td>
<td valign="top">

Any string of zero or more characters

</td>
</tr>
<tr>
<td valign="top">

\[\]

</td>
<td valign="top">

Any single character in the specified range or set

</td>
</tr>
<tr>
<td valign="top">

\[^\]

</td>
<td valign="top">

Any single character not in the specified range or set

</td>
</tr>
</table>



All other characters must match exactly.

For example, the following search condition is TRUE for any row where name starts with the letter a and has the letter b as its second-to-last character:

```
name LIKE 'a%b_'
```

If you specify an *<escape-expr\>*, then it must evaluate to a single character. The character can precede a percent, an underscore, a left square bracket, or another escape character in the *<pattern\>* to prevent the special character from having its special meaning. When escaped in this manner, a percent matches a percent, and an underscore matches an underscore.



<a name="loioa4fd6d2984f21015a71d97606b86f4f2__iq_refbb_87"/>

## Supported Patterns

All patterns of 126 characters or less are supported.

Some patterns between 127 and 254 characters are supported, but only under certain circumstances. See the following subsections for examples.

All patterns 255 characters or greater are not supported.



<a name="loioa4fd6d2984f21015a71d97606b86f4f2__section_tpg_4lb_x1b"/>

## Examples – Patterns Between 127 and 254 Characters



### Example 1

Under specific circumstances where adjacent constant characters exist in your pattern, patterns of length between 127 and 254 characters are supported. Each constant character in the string pattern requires 2 bytes, even if the character is a single-byte character. The string pattern in the LIKE predicate must be less than 256 bytes \(or 255/2 characters\) or else the following error appears:

```
There was an error reading the results of the SQL statement.
                        The displayed results may be incorrect or incomplete.
                        Cannot compile Like pattern: either bad pattern or pattern too long.
```

Data lake Relational Engine collapses adjacent constant characters into a single character. For example, consider the following LIKE predicate with a string length of 130 characters:

```
select col2 from tablen where col2 like
                        '123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456%%%%' ;
```

Data lake Relational Engine collapses the four adjacent constant characters %%%% at the end of the string into one % character, thereby reducing the length of the string from 130 characters to 127. This is less than the maximum of 256 bytes \(or 255/2 characters\), and no error is generated.

Therefore, if your LIKE predicate contains adjacent constants in the string, patterns of length between 127 and 254 characters are supported as long as the total length of the collapsed string is less than 256 bytes \(or 255/2 characters\).



### Example 2

In this example, the constant characters 7890 replace the four adjacent constant characters %%%% at the end of the 130-character LIKE predicate:

```
select col2 from tablen where col2 like
                        '1234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890' ;
```

In this case, no characters are collapsed. The character string length remains at 130 characters and data lake Relational Engine generates an error.



### Example 3

In this example, four adjacent underscores \_\_\_\_ \(special characters\) replace the four constant characters %%%% at the end of the 130-character LIKE predicate:

```
select col2 from tablen where col2 like
                        '123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456____' ;
```

Data lake Relational Engine does not collapse adjacent special characters. The string length remains at 130 characters and data lake Relational Engine generates an error.



### Example 4

In this example, the range \[1-3\] replaces the four constant characters %%%% at the end of the 130-character LIKE predicate:

```
select col2 from tablen where col2 like
                        '123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456[1-3]' ;
```

The length of the LIKE predicate in bytes is calculated as follows: 126 \(for the constant characters\) \* 2 + 1 \(for the 1 in brackets\) + 1 \( for the 3 in brackets\) + 2 \( for the Set state and Range state expression\).

This equals 256 bytes, and therefore data lake Relational Engine generates an error.



<a name="loioa4fd6d2984f21015a71d97606b86f4f2__iq_refbb_92"/>

## Searching for One of a Set of Characters

You can specify a set of characters to look for by listing the characters inside square brackets. For example, the following condition finds the strings smith and smyth:

```
LIKE 'sm[iy]th'
```



<a name="loioa4fd6d2984f21015a71d97606b86f4f2__iq_refbb_93"/>

## Searching for One of a Range of Characters

Specify a range of characters to look for by listing the ends of the range inside square brackets, separated by a hyphen. For example, the following condition finds the strings bough and rough, but not tough:

```
LIKE '[a-r]ough'
```

The range of characters \[a-z\] is interpreted as “greater than or equal to a, and less than or equal to z,” where the greater than and less than operations are carried out within the collation of the database. For information on ordering of characters within a collation, see *Selecting a Collation to Support a Specific Locale* in SAP HANA Cloud, Data Lake Administration Guide for Data Lake Relational Engine.

The lower end of the range must precede the higher end of the range. For example, a LIKE condition containing the expression \[z-a\] returns no rows, because no character matches the \[z-a\] range.

Unless the database is created as case-sensitive, the range of characters is case-insensitive. For example, the following condition finds the strings Bough, rough, and TOUGH:

```
LIKE '[a-z]ough'
```

If the database is created as a case-sensitive database, then the search condition is case-sensitive also.



<a name="loioa4fd6d2984f21015a71d97606b86f4f2__iq_refbb_94"/>

## Combining Searches for Ranges and Sets

You can combine ranges and sets within square brackets. For example, the following condition finds the strings bough, rough, and tough:

```
LIKE '[a-rt]ough'
```

The bracket \[a-mpqs-z\] is interpreted as “exactly one character that is either in the range a to m inclusive, or is p, or is q, or is in the range s to z inclusive.”



<a name="loioa4fd6d2984f21015a71d97606b86f4f2__iq_refbb_95"/>

## Searching for One Character Not in a Range

Use the caret character \(^\) to specify a range of characters that is excluded from a search. For example, the following condition finds the string tough, but not the strings rough, or bough:

```
LIKE '[^a-r]ough'
```

The caret negates the entire contents of the brackets. For example, the bracket \[^a-mpqs-z\] is interpreted as “exactly one character that is not in the range a to m inclusive, is not p, is not q, and is not in the range s to z inclusive.”



<a name="loioa4fd6d2984f21015a71d97606b86f4f2__iq_refbb_96"/>

## Special Cases of Ranges and Sets

Any single character in square brackets indicates that character. For example, \[a\] matches just the character a. \[^\] matches just the caret character, \[%\] matches only the percent character \(the percent character does not act as a wildcard character in this context\), and \[\_\] matches just the underscore character. Also, \[\[\] matches only the character \[.

Other special cases are:

-   The expression \[a-\] matches either of the characters a or -.
-   The expression \[\] is never matched and always returns no rows.
-   The expressions \[ or \[abp-q are ill-formed expressions, and give syntax errors.
-   You cannot use wildcard characters inside square brackets. The expression \[a%b\] finds one of a, %, or b.
-   You cannot use the caret character to negate ranges except as the first character in the bracket. The expression \[a^b\] finds one of a, ^, or b.



<a name="loioa4fd6d2984f21015a71d97606b86f4f2__iq_refbb_97"/>

## Compatibility

The ESCAPE clause is supported by data lake Relational Engine only.

> ### Note:  
> For information on support of the LIKE predicate with large object data and variables, see *Unstructured Data Queries* in SAP HANA Cloud, Data Lake Administration Guide for Data Lake Relational Engine.

**Related Information**  


[LOCATE Function \[String\] for Data Lake Relational Engine](../050-system-sql-functions/locate-function-string-for-data-lake-relational-engine-a55fae8.md "Returns the position of one string within another.")

[PATINDEX Function \[String\] for Data Lake Relational Engine](../050-system-sql-functions/patindex-function-string-for-data-lake-relational-engine-a56c8f8.md "Returns the starting position of the first occurrence of a specified pattern.")

[Selecting a Collation to Support a Specific Locale](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_4_QRC/en-US/a7552a1284f21015bc9ae70deba5bbf8.html "Address character set issues properly by using the collation, which best supports the locale.") :arrow_upper_right:

[Unstructured Data Queries](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_4_QRC/en-US/a5f84d4284f21015aa65c9ccbfed3414.html "Learn about querying large object data, including the full text search capability that handles unstructured and semistructured data.") :arrow_upper_right:

