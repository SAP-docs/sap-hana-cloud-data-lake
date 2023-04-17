<!-- loio537823cafa6a4fd2b934ca737ae215bf -->

# Reserved Words \[SAP HANA Database\]

Reserved words have a special meaning to the SQL parser and can’t be used when defining an identifier.

The following list provides you with the current reserved words for the SAP HANA database. You can obtain this list by querying the RESERVED\_KEYWORDS system view:

```
SELECT * FROM RESERVED_KEYWORDS ORDER BY RESERVED_KEYWORD;
```

In addition to the following SAP HANA database reserved keywords, avoid using the reserved keywords from the most recent ANSI SQL standard to ensure the compatibility of your SQL statements. However, if you do use these reserved words, we recommend placing them in uppercase and delimiting them with double quotation marks to ensure compatibility.

```
ALL
ALTER
ARRAY
AS
AT
AUTHORIZATION
BEFORE
BEGIN
BETWEEN
BOTH
BY
CASE
CHAR
COLLATE
CONDITION
CONNECT
CROSS
CUBE
CURRENT_CONNECTION
CURRENT_DATE
CURRENT_SCHEMA
CURRENT_TIME
CURRENT_TIMESTAMP
CURRENT_TRANSACTION_ISOLATION_LEVEL
CURRENT_USER
CURRENT_UTCDATE
CURRENT_UTCTIME
CURRENT_UTCTIMESTAMP
CURRVAL
CURSOR
DECLARE
DISTINCT
ELSE
ELSEIF
EMPTY
END
EXCEPT
EXCEPTION
EXEC
FALSE
FILTER
FOR
FROM
FULL
GROUP
GROUPING
HAVING
IF
IN
INNER
INOUT
INTERSECT
INTO
IS
JOIN
LATERAL
LEADING
LEFT
LIMIT
LOOP
MINUS
NATURAL
NCHAR
NEXTVAL
NO
NOT
NULL
OF
ON
ORDER
OUT
OVER
PRIOR
RECURSIVE
RETURN
RETURNS
REVERSE
RIGHT
ROLLUP
ROW
ROWID
SELECT
SESSION_USER
SET
SQL
START
SYSUUID
TABLE
TABLESAMPLE
TO
TOP
TRAILING
TRUE
UNION
UNKNOWN
UNNEST
USING
UTCTIMESTAMP
VALUES
WHEN
WHERE
WHILE
WINDOW
WITH
WITHIN
```

**Related Information**  


[Reserved Words in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../010-sql-language-elements/reserved-words-in-data-lake-relational-engine-sap-hana-db-managed-2bbe71e.md "Some keywords in SQL are also reserved words.")

