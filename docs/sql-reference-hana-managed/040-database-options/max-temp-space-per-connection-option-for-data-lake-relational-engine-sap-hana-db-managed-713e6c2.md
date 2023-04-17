<!-- loio713e6c2a4c594b22ae18a449e8ecd9dc -->

# MAX\_TEMP\_SPACE\_PER\_CONNECTION Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Limits temporary store space used per connection.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loio713e6c2a4c594b22ae18a449e8ecd9dc__section_xng_bbz_3sb"/>

## Default

0 \(no limit on temporary store usage\)



<a name="loio713e6c2a4c594b22ae18a449e8ecd9dc__section_bts_2bz_3sb"/>

## Remarks

By controlling space per connection, this option enables DBAs to manage the space for both loads and queries. If the connection exceeds the run time quota specified by `MAX_TEMP_SPACE_PER_CONNECTION`, data lake Relational Engine rolls back the current statement and returns this message to the IQ message file or client user:

```
The current operation has been canceled: Max_Temp_Space_Per_Connection exceeded
```

Conditions that may fill the buffer cache include read or write errors, lack of main or temp space, or being out of memory. Data lake Relational Engine may return the first error encountered in these situations and the DBA must determine the appropriate solution.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[IDENTITY\_INSERT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](identity-insert-option-for-data-lake-relational-engine-sap-hana-db-managed-3122a9a.md "Enables users to insert values into or to update an IDENTITY or AUTOINCREMENT column.")

