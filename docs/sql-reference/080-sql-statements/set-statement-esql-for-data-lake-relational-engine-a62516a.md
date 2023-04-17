<!-- loioa62516a184f210159f83bce20c1b607c -->

# SET Statement \[ESQL\] for Data Lake Relational Engine

Assigns a value to a SQL variable.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
SET <identifier> = <expression>
```



<a name="loioa62516a184f210159f83bce20c1b607c__IQ_Usage"/>

## Remarks

The SET statement assigns a new value to a variable. The variable must have been previously created by using a CREATE VARIABLE statement or DECLARE statement, or it must be an OUTPUT parameter for a procedure. The variable name can optionally use the Transact-SQL convention of an @ sign preceding the name. For example: Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(`SET @localvar = 42`.

A variable can be used in a SQL statement anywhere a column name is allowed. If a column name exists with the same name as the variable, then the column value is used.

The *<owner\>* specification is only for use when setting owned database-scope variables.

Variables are necessary for creating large text or binary objects for INSERT or UPDATE statements from Embedded SQL programs because Embedded SQL host variables are limited to 32767 bytes.

Variables are local to the current connection and disappear when you disconnect from the database or use the DROP VARIABLE statement. They are not affected by COMMIT or ROLLBACK statements.

If you set a database-scope variable, however, the variable persists after a disconnect. When the database is restarted, the value of a database-scope variable reverts to NULL or its default, if defined. The SYSDATABASEVARIABLE system view contains a list of all database-scope variables and their initial values.

You cannot set a database-scope variable owned by another user.



<a name="loioa62516a184f210159f83bce20c1b607c__IQ_Permissions"/>

## Privileges

-   If you own the database-scope variable, no additional privilege is required.
-   To set a database-scope variable owned by PUBLIC, requires the UPDATE PUBLIC DATABASE VARIABLE system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa62516a184f210159f83bce20c1b607c__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – not supported. In SAP Adaptive Server Enterprise, variables are assigned using the `SELECT`Sections in this topic are minimized. To expand or recollapse a section, click the statement with no table, a Transact-SQL syntax that is also supported by data lake Relational Engine. The `SET` statement is used to set database options in SAP ASE.



<a name="loioa62516a184f210159f83bce20c1b607c__IQ_Examples"/>

## Examples

-   This code fragment inserts a large text value into the database:

    ```
    EXEC SQL BEGIN DECLARE SECTION;
    char buffer[5001];
    EXEC SQL END DECLARE SECTION;
    
    
    EXEC SQL CREATE VARIABLE hold_text VARCHAR;
    EXEC SQL SET hold_text = '';
    for(;;) {
    	/* read some data into buffer ... */
    	size = fread( buffer, 1, 5000, fp );
    	if( size <= 0 ) break;
    	
    	/* buffer must be null-terminated */
    	buffer[size] = '\0';
    	/* add data to blob using concatenation */
    	EXEC SQL SET hold_text = hold_text || :buffer;
    }
    EXEC SQL INSERT INTO some_table VALUES ( 1, hold_text );
    EXEC SQL DROP VARIABLE hold_text;
    ```

-   This code fragment inserts a large binary value into the database:

    ```
    EXEC SQL BEGIN DECLARE SECTION;
    DECL_BINARY( 5000 ) buffer;
    EXEC SQL END DECLARE SECTION;
    EXEC SQL CREATE VARIABLE hold_blob LONG BINARY;
    EXEC SQL SET hold_blob = '';
    for(;;) {
    	/* read some data into buffer ... */
    	size = fread( &(buffer.array), 1, 5000, fp );
    	if( size <= 0 ) break;
    	buffer.len = size;
    
    
    	/* add data to blob using concatenation
    		Note that concatenation works for 
    		binary data too! */
    	EXEC SQL SET hold_blob = hold_blob || :buffer;
    }
    EXEC SQL INSERT INTO some_table VALUES ( 1, hold_blob );
    EXEC SQL DROP VARIABLE hold_blob;
    ```

-   This simple example shows the creation of a variable called birthday, and sets the date to CURRENT DATE:

    ```
    CREATE VARIABLE @birthday DATE;
    SET @birthday = CURRENT DATE;
    ```

-   The following code fragment inserts a large text value into the database:

    ```
    size_t  size;
    FILE *  fp;
    
    EXEC SQL BEGIN DECLARE SECTION;
    DECL_VARCHAR( 5000 ) buffer;
    EXEC SQL END DECLARE SECTION;
    
    fp = fopen( "blob.dat", "r" );
    EXEC SQL CREATE VARIABLE hold_blob LONG VARCHAR;
    EXEC SQL SET hold_blob = '';
    for(;;) {
        size = fread( (void *)buffer.array, 1, 5000, fp );
        if( size <= 0 ) break;
        buffer.len = (a_sql_ulen) size;
        EXEC SQL SET hold_blob = hold_blob || :buffer;
    }
    EXEC SQL INSERT INTO some_table VALUES( 1, hold_blob );
    EXEC SQL COMMIT;
    EXEC SQL DROP VARIABLE hold_blob;
    fclose( fp );
    ```


**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[CREATE VARIABLE Statement for Data Lake Relational Engine](create-variable-statement-for-data-lake-relational-engine-a619d63.md "Creates data type or a connection- or database-scope variable.")

[DROP VARIABLE Statement for Data Lake Relational Engine](drop-variable-statement-for-data-lake-relational-engine-816f992.md "Drops a connection-scope SQL variable.")

