<!-- loio0023beaa84b743a2a3341296e49f2b8c -->

# REMOTE\_EXECUTE Usage Examples for Setting Database Options

Set data lake Relational Engine database options.



When syntax within the REMOTE\_EXECUTE procedure contains single quotes, they must themselves be enclosed in single quotes. For example, ' '<syntax\>' '. 

This statement temporarily sets the DATE\_FORMAT option to YYY-DD-MMM.

```
CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE (' 
   SET TEMPORARY OPTION DATE_FORMAT = "YYYY-DD-MMM" 
');
```

This statement turns on the CONVERSION\_ERROR option.

```
CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE (' 
   SET OPTION SYSRDL#CG.CONVERSION_ERROR = "ON" 
');
```

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

