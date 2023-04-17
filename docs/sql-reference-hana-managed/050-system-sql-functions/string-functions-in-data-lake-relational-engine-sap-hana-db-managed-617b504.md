<!-- loio617b504c77ea47758db2d856e10486be -->

# String Functions in Data Lake Relational Engine \(SAP HANA DB-Managed\)

String functions perform conversion, extraction, or manipulation operations on strings, or return information about strings.



When working in a multibyte character set, check carefully whether the function being used returns information concerning characters or bytes.

Most of the string functions accept binary data \(hexadecimal strings\) in the *<string-expr\>* parameter, but some of the functions, such as LCASE, UCASE, LOWER, and LTRIM, expect the string expression to be a character string.

Unless you supply a constant LENGTH argument to a function that produces a LONG VARCHAR result \(such as SPACE or REPEAT\), the default length is the maximum allowed.

Data lake Relational Engine queries containing one or more of these functions might return one of the following errors:

```
Error -1009080: Key doesn't fit on a single database page: 65560(4, 1)
```

```
Error -1009119: Record size too large for database page size
```

For example:

```
SELECT COUNT(*) FROM test1 a WHERE (a.col1 + SPACE(4-LENGTH(a.col1))
  + a.col2 + space(2- LENGTH(a.col2))) IN (SELECT (b.col3) FROM test1 b);
```

To avoid such errors, cast the function result with an appropriate maximum length; for example:

```
SELECT COUNT(*) FROM test1 a WHERE (a.col1 + CAST(SPACE(4-LENGTH(a.col1)) 
  AS VARCHAR(4)) + a.col2 + CAST(SPACE(2-LENGTH (a.col2)) AS VARCHAR(4)))
  IN (SELECT (b.col3) FROM test1 b);
```

The errors are more likely with a page size of 64K or a multibyte collation.



The following functions are available:

-   [AES\_ENCRYPT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](aes-encrypt-function-for-data-lake-relational-engine-sap-hana-db-managed-4689e70.md)
-   [AES\_DECRYPT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](aes-decrypt-function-for-data-lake-relational-engine-sap-hana-db-managed-a5dc84d.md)
-   [ASCII Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](ascii-function-for-data-lake-relational-engine-sap-hana-db-managed-554cede.md)
-   [BIT\_LENGTH Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](bit-length-function-for-data-lake-relational-engine-sap-hana-db-managed-7d6e331.md)
-   [BYTE\_INSERTSTR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](byte-insertstr-function-for-data-lake-relational-engine-sap-hana-db-managed-a8656a2.md)
-   [BYTE\_LENGTH Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](byte-length-function-for-data-lake-relational-engine-sap-hana-db-managed-da0bd30.md)
-   [BYTE\_LENGTH64 Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](byte-length64-function-for-data-lake-relational-engine-sap-hana-db-managed-16450cf.md)
-   [BYTE\_LOCATE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](byte-locate-function-for-data-lake-relational-engine-sap-hana-db-managed-65d4388.md)
-   [BYTE\_REPLACE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](byte-replace-function-for-data-lake-relational-engine-sap-hana-db-managed-ae74fd6.md)
-   [BYTE\_STUFF Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](byte-stuff-function-for-data-lake-relational-engine-sap-hana-db-managed-538f342.md)
-   [BYTE\_SUBSTR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](byte-substr-function-for-data-lake-relational-engine-sap-hana-db-managed-e7559cd.md)
-   [BYTE\_SUBSTR64 and BYTE\_SUBSTR Functions for Data Lake Relational Engine \(SAP HANA DB-Managed\)](byte-substr64-and-byte-substr-functions-for-data-lake-relational-engine-sap-hana-db-mana-64a8d38.md)
-   [CHAR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](char-function-for-data-lake-relational-engine-sap-hana-db-managed-6c2f4cf.md)
-   [CHAR\_LENGTH Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](char-length-function-for-data-lake-relational-engine-sap-hana-db-managed-c440e3a.md)
-   [CHAR\_LENGTH64 Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](char-length64-function-for-data-lake-relational-engine-sap-hana-db-managed-54f22f3.md)
-   [CHARINDEX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](charindex-function-for-data-lake-relational-engine-sap-hana-db-managed-ae49951.md)
-   [DIFFERENCE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](difference-function-for-data-lake-relational-engine-sap-hana-db-managed-3b8bafe.md)
-   [ENCRYPT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](encrypt-function-for-data-lake-relational-engine-sap-hana-db-managed-ec24782.md)
-   [INSERTSTR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](insertstr-function-for-data-lake-relational-engine-sap-hana-db-managed-064a64c.md)
-   [LCASE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](lcase-function-for-data-lake-relational-engine-sap-hana-db-managed-d968d3b.md)
-   [LEFT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](left-function-for-data-lake-relational-engine-sap-hana-db-managed-7d6ec6d.md)
-   [LEN Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](len-function-for-data-lake-relational-engine-sap-hana-db-managed-a895aab.md)
-   [LENGTH Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](length-function-for-data-lake-relational-engine-sap-hana-db-managed-ae555cf.md)
-   [LOCATE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](locate-function-for-data-lake-relational-engine-sap-hana-db-managed-ea53f0b.md)
-   [LOWER Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](lower-function-for-data-lake-relational-engine-sap-hana-db-managed-3ad1772.md)
-   [LPAD Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](lpad-function-for-data-lake-relational-engine-sap-hana-db-managed-64302f8.md)
-   [LTRIM Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](ltrim-function-for-data-lake-relational-engine-sap-hana-db-managed-ccfb4d6.md)
-   [OCTET\_LENGTH Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](octet-length-function-for-data-lake-relational-engine-sap-hana-db-managed-5a0cde7.md)
-   [PATINDEX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](patindex-function-for-data-lake-relational-engine-sap-hana-db-managed-073fd34.md)
-   [READ\_SERVER\_FILE Function \[String\] for Data Lake Relational Engine \(SAP HANA DB-Managed\)](read-server-file-function-string-for-data-lake-relational-engine-sap-hana-db-managed-0eaddd0.md)
-   [REPEAT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](repeat-function-for-data-lake-relational-engine-sap-hana-db-managed-0248da6.md)
-   [REPLACE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](replace-function-for-data-lake-relational-engine-sap-hana-db-managed-b8f3ed4.md)
-   [REPLICATE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](replicate-function-for-data-lake-relational-engine-sap-hana-db-managed-1cb52e2.md)
-   [REVERSE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](reverse-function-for-data-lake-relational-engine-sap-hana-db-managed-3310f4b.md)
-   [RIGHT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](right-function-for-data-lake-relational-engine-sap-hana-db-managed-03fba12.md)
-   [RPAD Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](rpad-function-for-data-lake-relational-engine-sap-hana-db-managed-6c4ea24.md)
-   [RTRIM Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](rtrim-function-for-data-lake-relational-engine-sap-hana-db-managed-3b49f57.md)
-   [SIMILAR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](similar-function-for-data-lake-relational-engine-sap-hana-db-managed-328e90f.md)
-   [SORTKEY Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sortkey-function-for-data-lake-relational-engine-sap-hana-db-managed-66b4419.md)
-   [SOUNDEX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](soundex-function-for-data-lake-relational-engine-sap-hana-db-managed-74cbdbe.md)
-   [SPACE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](space-function-for-data-lake-relational-engine-sap-hana-db-managed-ad08141.md)
-   [STR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](str-function-for-data-lake-relational-engine-sap-hana-db-managed-6152b16.md)
-   [STR\_REPLACE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](str-replace-function-for-data-lake-relational-engine-sap-hana-db-managed-d0e0474.md)
-   [STRING Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](string-function-for-data-lake-relational-engine-sap-hana-db-managed-4b63110.md)
-   [STRTOUUID Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](strtouuid-function-for-data-lake-relational-engine-sap-hana-db-managed-5572345.md)
-   [STUFF Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](stuff-function-for-data-lake-relational-engine-sap-hana-db-managed-61e8de5.md)
-   [SUBSTRING Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](substring-function-for-data-lake-relational-engine-sap-hana-db-managed-f114d35.md)
-   [SUBSTRING64 Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](substring64-function-for-data-lake-relational-engine-sap-hana-db-managed-4ff0a13.md)
-   [TRIM Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](trim-function-for-data-lake-relational-engine-sap-hana-db-managed-d07890f.md)
-   [UCASE\_syntax Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](ucase-syntax-function-for-data-lake-relational-engine-sap-hana-db-managed-3c1a297.md)
-   [UPPER Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](upper-function-for-data-lake-relational-engine-sap-hana-db-managed-1084333.md)
-   [UUIDTOSTR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](uuidtostr-function-for-data-lake-relational-engine-sap-hana-db-managed-60f4cba.md)

