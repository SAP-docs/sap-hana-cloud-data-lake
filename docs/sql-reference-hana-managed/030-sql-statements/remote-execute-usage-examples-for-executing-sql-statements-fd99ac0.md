<!-- loiofd99ac0ce9914c7695488ca4b2fa70f5 -->

# REMOTE\_EXECUTE Usage Examples for Executing SQL Statements

Execute a data lake Relational Engine SQL statement by embedding the statement in the REMOTE\_EXECUTE procedure.



When syntax within the REMOTE\_EXECUTE procedure contains single quotes, they must themselves be enclosed in single quotes. For example, ' '<syntax\>' '.



This statement creates table T2 in relational container CONTAINER1.

```
CALL [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.REMOTE_EXECUTE ('
   CREATE TABLE T2 (A INT, B INT)
');
```



This statement creates the data lake Relational Engine view VIEW\_T1 in relational container CONTAINER1.

```
CALL [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.REMOTE_EXECUTE ('
   CREATE VIEW VIEW_T1 AS SELECT * FROM T1
');
```



This statement creates a data lake Relational Engine HG index on columns A and B on table T1 in relational container CONTAINER1.

```
CALL [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.REMOTE_EXECUTE ('
   CREATE HG INDEX INDEX1_T1 ON T1 (A, B)
');
```

