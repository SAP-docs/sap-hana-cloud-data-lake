<!-- loioa52d1d9284f21015a01087134ebb1e34 -->

# String Functions in Data Lake Relational Engine

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

-   [AES\_ENCRYPT Function \[String\] for Data Lake Relational Engine](aes-encrypt-function-string-for-data-lake-relational-engine-a4c3260.md)
-   [AES\_DECRYPT Function \[String\] for Data Lake Relational Engine](aes-decrypt-function-string-for-data-lake-relational-engine-a4c35f4.md)
-   [ASCII Function \[String\] for Data Lake Relational Engine](ascii-function-string-for-data-lake-relational-engine-a533e3a.md)
-   [BIT\_LENGTH Function \[String\] for Data Lake Relational Engine](bit-length-function-string-for-data-lake-relational-engine-a537928.md)
-   [BYTE\_INSERTSTR Function \[String\] for Data Lake Relational Engine](byte-insertstr-function-string-for-data-lake-relational-engine-81f411c.md)
-   [BYTE\_LENGTH Function \[String\] for Data Lake Relational Engine](byte-length-function-string-for-data-lake-relational-engine-a53816b.md)
-   [BYTE\_LENGTH64 Function \[String\] for Data Lake Relational Engine](byte-length64-function-string-for-data-lake-relational-engine-a538947.md)
-   [BYTE\_LOCATE Function \[String\] for Data Lake Relational Engine](byte-locate-function-string-for-data-lake-relational-engine-6b6d91a.md)
-   [BYTE\_REPLACE Function \[String\] for Data Lake Relational Engine](byte-replace-function-string-for-data-lake-relational-engine-4d5eb9f.md)
-   [BYTE\_STUFF Function \[String\] for Data Lake Relational Engine](byte-stuff-function-string-for-data-lake-relational-engine-81f4257.md)
-   [BYTE\_SUBSTR Function \[String\] for Data Lake Relational Engine](byte-substr-function-string-for-data-lake-relational-engine-81f42f4.md)
-   [BYTE\_SUBSTR64 and BYTE\_SUBSTR Functions \[String\] for Data Lake Relational Engine](byte-substr64-and-byte-substr-functions-string-for-data-lake-relational-engine-a539151.md)
-   [CHAR function \[String\] for Data Lake Relational Engine](char-function-string-for-data-lake-relational-engine-a53b50f.md)
-   [CHAR\_LENGTH Function \[String\] for Data Lake Relational Engine](char-length-function-string-for-data-lake-relational-engine-a53bd3d.md)
-   [CHAR\_LENGTH64 Function \[String\] for Data Lake Relational Engine](char-length64-function-string-for-data-lake-relational-engine-a53c545.md)
-   [CHARINDEX Function \[String\] for Data Lake Relational Engine](charindex-function-string-for-data-lake-relational-engine-a53cde2.md)
-   [CHARINDEX Function \[String\] for Data Lake Relational Engine](charindex-function-string-for-data-lake-relational-engine-a53cde2.md)

-   [DECRYPT Function \[String\] for Data Lake Relational Engine](decrypt-function-string-for-data-lake-relational-engine-81f6b4a.md)

-   [DIFFERENCE Function \[String\] for Data Lake Relational Engine](difference-function-string-for-data-lake-relational-engine-a54d8aa.md)
-   [ENCRYPT Function \[String\] for Data Lake Relational Engine](encrypt-function-string-for-data-lake-relational-engine-81f72ce.md)
-   [GRAPHICAL\_PLAN Function \[String\] for Data Lake Relational Engine](graphical-plan-function-string-for-data-lake-relational-engine-a553c53.md)
-   [INSERTSTR Function \[String\] for Data Lake Relational Engine](insertstr-function-string-for-data-lake-relational-engine-a558eff.md)
-   [LCASE Function \[String\] for Data Lake Relational Engine](lcase-function-string-for-data-lake-relational-engine-a55c82d.md)
-   [LEFT Function \[String\] for Data Lake Relational Engine](left-function-string-for-data-lake-relational-engine-a55d883.md)
-   [LEN Function \[String\] for Data Lake Relational Engine](len-function-string-for-data-lake-relational-engine-a55e08c.md)
-   [LENGTH Function \[String\] for Data Lake Relational Engine](length-function-string-for-data-lake-relational-engine-a55ea65.md)
-   [LOCATE Function \[String\] for Data Lake Relational Engine](locate-function-string-for-data-lake-relational-engine-a55fae8.md)
-   [LOWER Function \[String\] for Data Lake Relational Engine](lower-function-string-for-data-lake-relational-engine-a561324.md)
-   [LPAD Function \[String\] for Data Lake Relational Engine](lpad-function-string-for-data-lake-relational-engine-7bf4b42.md)
-   [LTRIM Function \[String\] for Data Lake Relational Engine](ltrim-function-string-for-data-lake-relational-engine-a561eaf.md)
-   [OCTET\_LENGTH Function \[String\] for Data Lake Relational Engine](octet-length-function-string-for-data-lake-relational-engine-a56c053.md)
-   [PATINDEX Function \[String\] for Data Lake Relational Engine](patindex-function-string-for-data-lake-relational-engine-a56c8f8.md)
-   [READ\_SERVER\_FILE Function \[String\] for Data Lake Relational Engine](read-server-file-function-string-for-data-lake-relational-engine-81fb732.md)
-   [REPEAT Function \[String\] for Data Lake Relational Engine](repeat-function-string-for-data-lake-relational-engine-a579104.md)
-   [REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md)
-   [REPLICATE Function \[String\] for Data Lake Relational Engine](replicate-function-string-for-data-lake-relational-engine-a57a156.md)
-   [REVERSE Function \[String\] for Data Lake Relational Engine](reverse-function-string-for-data-lake-relational-engine-a57a972.md)
-   [RIGHT Function \[String\] for Data Lake Relational Engine](right-function-string-for-data-lake-relational-engine-a57b364.md)
-   [RPAD Function \[String\] for Data Lake Relational Engine](rpad-function-string-for-data-lake-relational-engine-3a8714b.md)
-   [RTRIM Function \[String\] for Data Lake Relational Engine](rtrim-function-string-for-data-lake-relational-engine-a57d411.md)
-   [SIMILAR Function \[String\] for Data Lake Relational Engine](similar-function-string-for-data-lake-relational-engine-a57f56c.md)
-   [SORTKEY Function \[String\] for Data Lake Relational Engine](sortkey-function-string-for-data-lake-relational-engine-a5805dd.md)
-   [SOUNDEX Function \[String\] for Data Lake Relational Engine](soundex-function-string-for-data-lake-relational-engine-a580dde.md)
-   [SPACE Function \[String\] for Data Lake Relational Engine](space-function-string-for-data-lake-relational-engine-a5815e2.md)
-   [STR Function \[String\] for Data Lake Relational Engine](str-function-string-for-data-lake-relational-engine-a584f54.md)
-   [STR\_REPLACE Function \[String\] for Data Lake Relational Engine](str-replace-function-string-for-data-lake-relational-engine-a5857e0.md)
-   [STRING Function \[String\] for Data Lake Relational Engine](string-function-string-for-data-lake-relational-engine-a586010.md)
-   [STRTOUUID Function \[String\] for Data Lake Relational Engine](strtouuid-function-string-for-data-lake-relational-engine-a58683c.md)
-   [STUFF Function \[String\] for Data Lake Relational Engine](stuff-function-string-for-data-lake-relational-engine-a58705b.md)
-   [SUBSTRING Function \[String\] for Data Lake Relational Engine](substring-function-string-for-data-lake-relational-engine-a58787e.md)
-   [SUBSTRING64 Function \[String\] for Data Lake Relational Engine](substring64-function-string-for-data-lake-relational-engine-a588072.md)
-   [TRIM Function \[String\] for Data Lake Relational Engine](trim-function-string-for-data-lake-relational-engine-a58b326.md)
-   [UCASE Function \[String\] for Data Lake Relational Engine](ucase-function-string-for-data-lake-relational-engine-a58c382.md)
-   [UPPER Function \[String\] for Data Lake Relational Engine](upper-function-string-for-data-lake-relational-engine-a58cbc0.md)
-   [UUIDTOSTR Function \[String\] for Data Lake Relational Engine](uuidtostr-function-string-for-data-lake-relational-engine-a58e3ff.md)

