<!-- loio0023beaa84b743a2a3341296e49f2b8c -->

# REMOTE\_EXECUTE Guidance and Examples for Setting Permanent Database Options

Use REMOTE\_EXECUTE to permanently set data lake Relational Engine database options in a data lake Relational Engine integrated withSAP HANA database.



> ### Caution:  
> You cannot use the REMOTE\_EXECUTE procedure to temporarily set a database option in a data lake Relational Engine integrated withSAP HANA database. For this, use the [SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](https://help.sap.com/docs/hana-cloud-data-lake/sql-reference-for-data-lake-relational-engine-sap-hana-db-managed/set-temporary-option-procedure-for-sap-hana-database?state=DRAFT&version=2023_2_QRC).

To use REMOTE\_EXECUTE requires one of the following:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

If syntax within the REMOTE\_EXECUTE procedure contains single quotes, then the quoted syntax must itself be enclosed in single quotes. For example, '<syntax\>' becomes ''<syntax\>''. Though they may appear similar, do not use a double quote in place of two single quotes.

For example, this statement permanently sets the DATE\_FORMAT to YYY-DD-MMM. Since the date format parameter is enclosed in single quotes \('YYYY-DD-MMM'\), the parameter must be enclosed in second set of single quotes \(''YYYY-DD-MMM''\).

```
CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE (' 
   SET OPTION DATE_FORMAT = ''YYYY-DD-MMM'' 
');
```

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

