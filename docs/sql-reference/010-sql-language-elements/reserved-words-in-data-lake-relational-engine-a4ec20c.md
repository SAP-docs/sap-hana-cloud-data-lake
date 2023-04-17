<!-- loioa4ec20ca84f2101599e4ca641dea6f76 -->

# Reserved Words in Data Lake Relational Engine

Some keywords in SQL are also reserved words.



To use a reserved word in a SQL statement as an identifier, you enclose the word in double quotes. Many, but not all, of the keywords that appear in SQL statements are reserved words. For example, you must use the following syntax to retrieve the contents of a table named SELECT:

```
SELECT * FROM "SELECT"
```

If you are using Embedded SQL, then you can use the database library function sql\_needs\_quotes to determine whether a string requires quotation marks. A string requires quotes if it is a reserved word or if it contains a character not ordinarily allowed in an identifier.

This table lists the SQL reserved words in data lake Relational Engine. Because SQL is not case-sensitive with respect to keywords, each of the words in this table may appear in uppercase, lowercase, or any combination of the two. All strings that differ only in capitalization from these words are reserved words.

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


[Keywords in Data Lake Relational Engine](keywords-in-data-lake-relational-engine-a4eb80b.md "Each SQL statement contains one or more keywords.")

[Reserved Words in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/2bbe71e4f77a41cd81be468e2ac4b751.html "Some keywords in SQL are also reserved words.") :arrow_upper_right:
