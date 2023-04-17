<!-- loioa594815784f21015845dc1b4d3ce261c -->

# Integrity

Data lake Relational Engine supports both entity and referential integrity.

This has been implemented via the following two extensions to the `CREATE TABLE` and `ALTER TABLE` statements:

```
PRIMARY KEY ( <column-name>, ... )
[NOT NULL] FOREIGN KEY [<role-name>] 
				[(<column-name>, ...)]
			REFERENCES <table-name> [(<column-name>, ...)]
				[ CHECK ON COMMIT ]
```

The `PRIMARY KEY` clause declares the primary key for the relation. Data lake Relational Engine will then enforce the uniqueness of the primary key, and ensure that no column in the primary key contains the NULL value.

The `FOREIGN KEY` clause defines a relationship between this table and another table. This relationship is represented by a column \(or columns\) in this table, which must contain values in the primary key of another table. The system then ensures referential integrity for these columns; whenever these columns are modified or a row is inserted into this table, these columns are checked to ensure that either one or more is NULL or the values match the corresponding columns for some row in the primary key of the other table.

