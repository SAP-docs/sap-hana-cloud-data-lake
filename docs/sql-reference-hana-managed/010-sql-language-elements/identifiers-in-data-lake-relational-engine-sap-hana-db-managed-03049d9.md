<!-- loio03049d939200442693d576e880b340ef -->

# Identifiers in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Identifiers are names of objects in the database, such as user IDs, tables, and columns.



Identifiers have a maximum length of 128 bytes. They must be enclosed in double quotes or square brackets if any of these conditions are true:



-   The identifier contains spaces.
-   The first character of the identifier is not an alphabetic character \(as defined below\).
-   The identifier contains a reserved word.
-   The identifier contains characters other than alphabetic characters and digits.

    Alphabetic characters include the alphabet, as well as the underscore character \(\_\), at sign \(@\), number sign \(\#\), and dollar sign \($\). The database collation sequence dictates which characters are considered alphabetic or digit characters.




These characters are not allowed inside an identifier:

-   Double quotes \("\)
-   Control characters \(any character less than 0x20\)
-   Backslashes \(/\)
-   Square bracket, open \(\[\)
-   Square bracket, close \(\]\)
-   Back quote/grave accent \(\`\)

You can represent an apostrophe/single quote \('\) inside an identifier by following it with another apostrophe.

If the QUOTED\_IDENTIFIER database option is set to OFF, then double quotes are used to delimit SQL strings and cannot be used for identifiers. However, you can always use square brackets to delimit identifiers, regardless of the setting of QUOTED\_IDENTIFIER.

The default setting for the QUOTED\_IDENTIFIER option is OFF for Open Client and jConnect connections; otherwise the default is ON.

Identifiers cannot begin with the prefix '\_SAP\_' or '\_sap\_'. Identifier names are case insensitive.



<a name="loio03049d939200442693d576e880b340ef__section_py4_4gx_3sb"/>

## Limitations

Identifiers have the following limitations:

-   Table names cannot contain double quotes.
-   User names cannot contain double quote or semicolon characters \(single quote characters are allowed\).
-   Database names cannot contain double quote, single quote, and semicolon characters.
-   User names and database names cannot start or end with a space.
-   Dbspace names are always case-insensitive, regardless of the CASE IGNORE or CASE RESPECT specifications.

**Related Information**  


[Reserved Words in Data Lake Relational Engine \(SAP HANA DB-Managed\)](reserved-words-in-data-lake-relational-engine-sap-hana-db-managed-2bbe71e.md "Some keywords in SQL are also reserved words.")

[Identifiers in Data Lake Relational Engine \(SAP HANA DB-Managed\)](identifiers-in-data-lake-relational-engine-sap-hana-db-managed-03049d9.md "Identifiers are names of objects in the database, such as user IDs, tables, and columns.")

