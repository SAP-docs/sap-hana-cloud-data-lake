<!-- loio48315ef4d44b410f824da9993b5faee6 -->

# Send Dates and Times in Data Lake Relational Engine \(SAP HANA DB-Managed\)

You send dates and times to the database in a number of ways.



-   Using any interface, as a string
-   Using ODBC, as a TIMESTAMP structure
-   Using Embedded SQL, as a SQLDATETIME structure

When you send a time to the database as a string \(for the TIME data type\) or as part of a string \(for TIMESTAMP or DATE data types\), hours, minutes, and seconds must be separated by colons in the format *<hh\>*:*<mm\>*:*<ss\>*:*<sss\>*, but can appear anywhere in the string. As an option, a period can separate the seconds from fractions of a second, as in *<hh\>*:*<mm\>*:*<ss\>*.*<sss\>*. The following are valid and unambiguous strings for specifying times:

```
21:35 -- 24 hour clock if no am or pm specified
10:00pm -- pm specified, so interpreted as 12 hour clock
10:00 -- 10:00am in the absence of pm
10:23:32.234 -- seconds and fractions of a 
                    second included
```

When you send a date to the database as a string, conversion to a date is automatic. You can supply the string in one of two ways:

-   As a string of format *<yyyy/mm/dd\>* or *<yyyy-mm-dd\>*, which is interpreted unambiguously by the database
-   As a string interpreted according to the DATE\_ORDER database option

Date format strings cannot contain any multibyte characters. Only single-byte characters are allowed in a date/time/datetime format string, even when the collation order of the database is a multibyte collation order like 932JPN.

