<!-- loio2bbe71e4f77a41cd81be468e2ac4b751 -->

# Reserved Words in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Some keywords in SQL are also reserved words.



To use a reserved word in a SQL statement as an identifier, you enclose the word in double quotes. Many, but not all, of the keywords that appear in SQL statements are reserved words. For example, you must use the following syntax to retrieve the contents of a table named SELECT:

```
SELECT * FROM "SELECT";
```

If you are using Embedded SQL, then you can use the database library function sql\_needs\_quotes to determine whether a string requires quotation marks. A string requires quotes if it is a reserved word or if it contains a character not ordinarily allowed in an identifier.

SQL is not case-sensitive with respect to keywords. Each of the words in this list may appear in uppercase, lowercase, or any combination of the two. All strings that differ only in capitalization from these words are reserved words.

This list lists the SQL reserved words for data lake Relational Engine.

```
ADD
AES_DECRYPT
ALL
ALTER
AND
ANY
ARRAY
AS
ASC
ATTACH
BACKUP
BEGIN
BETWEEN
BIGINT
BINARY
BIT
BOTTOM
BREAK
BY
CALL
CAPABILITY
CASCADE
CASE
CAST
CHAR
CHAR_CONVERT
CHARACTER
CHECK
CHECKPOINT
CLEAR
CLOSE
COMMENT
COMMIT
COMPRESSED
CONFLICT
CONNECT
CONSTRAINT
CONTAINS
CONTINUE
CONVERT
CREATE
CROSS
CUBE
CURRENT
CURRENT_DATABASE_SCHEMA
CURRENT_TIMESTAMP
CURRENT_USER
CURSOR
DATE
DATETIMEOFFSET
DATETIMEX
DBSPACE
DEALLOCATE
DEC
DECIMAL
DECLARE
DEFAULT
DELETE
DELETING
DESC
DETACH
DISTINCT
DO
DOUBLE
DROP
DYNAMIC
ELSE
ELSEIF
ENCRYPTED
END
ENDIF
ESCAPE
EXCEPT
EXCEPTION
EXEC
EXECUTE
EXECUTING
EXECUTING_USER
EXISTING
EXISTS
EXTERNLOGIN
EXTRACT
FALSE FEATURE []
FETCH
FIRST
FLOAT
FOR
FORCE
FOREIGN
FORWARD
FROM
FULL
GOTO
GRANT
GROUP
HAVING
HOLDLOCK
IDENTIFIED
IF
IN
INDEX
INNER
INOUT
INSENSITIVE
INSERT
INSERTING
INSTALL
INSTEAD
INT
INTEGER
INTEGRATED
INTERSECT
INTO
INVOKING
INVOKING_USER
IQ
IS
ISOLATION
JOIN
JSON
KERBEROS
KEY
LATERAL
LEFT
LIKE
LIMIT
LOCK
LOGIN
LONG
MATCH
MEMBERSHIP
MERGE
MESSAGE
MODE
MODIFY
NATURAL
NCHAR
NEW
NO
NOHOLDLOCK
NOT
NOTIFY
NULL
NUMERIC
NVARCHAR
OF
OFF
ON
OPEN
OPENSTRING
OPENXML
OPTION
OPTIONS
OR
ORDER
OTHERS
OUT
OUTER
OVER
PASSTHROUGH
PIVOT
PRECISION
PREPARE
PRIMARY
PRINT
PRIVILEGES
PROC
PROCEDURE
PROCEDURE_OWNER
PUBLICATION
RAISERROR
READTEXT
REAL
REFERENCE
REFERENCES
REFRESH
RELEASE
REMOTE
REMOVE
RENAME
REORGANIZE
RESOURCE
RESTORE
RESTRICT
RETURN
REVOKE
RIGHT
ROLLBACK
ROLLUP
ROW
ROWTYPE
SAVE
SAVEPOINT
SCROLL
SELECT
SENSITIVE
SESSION
SESSION_USER
SET
SETUSER
SHARE
SMALLINT
SOME
SPATIAL
SQLCODE
SQLSTATE
START
STOP
SUBTRANS
SUBTRANSACTION
SYNCHRONIZE
TABLE
TEMPORARY
THEN
TIME
TIMELINE
TIMESTAMP
TINYINT
TO
TOP
TRAN
TREAT
TRIGGER
TRUE FEATURE []
TRUNCATE
TSEQUAL
UNBOUNDED
UNION
UNIQUE
UNIQUEIDENTIFIER
UNKNOWN
UNNEST
UNPIVOT
UNSIGNED
UPDATE
UPDATING
USER
USING
VALIDATE
VALUES
VARBINARY
VARBIT
VARCHAR
VARIABLE
VARRAY
VARYING
VIEW
WAIT
WAITFOR
WHEN
WHERE
WHILE
WINDOW
WITH
WITHIN
WORK
WRITETEXT
XML

```

**Related Information**  


[RESERVED\_KEYWORDS Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../040-database-options/reserved-keywords-option-for-data-lake-relational-engine-sap-hana-db-managed-991b4fb.md "Turns on individual keywords that are disabled by default.")

[Reserved Words in Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a4ec20ca84f2101599e4ca641dea6f76.html "Some keywords in SQL are also reserved words.") :arrow_upper_right:

[Keywords in Data Lake Relational Engine \(SAP HANA DB-Managed\)](keywords-in-data-lake-relational-engine-sap-hana-db-managed-ea6e823.md "Each SQL statement contains one or more keywords.")

[Reserved Words \[SAP HANA Database\]](../080-sap-hana-database-for-data-lake-relational-engine/reserved-words-sap-hana-database-537823c.md "Reserved words have a special meaning to the SQL parser and can’t be used when defining an identifier.")

