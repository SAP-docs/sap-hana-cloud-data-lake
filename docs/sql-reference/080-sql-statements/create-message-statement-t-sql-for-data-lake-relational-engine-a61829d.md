<!-- loioa61829d784f210158a99f4e03b39b150 -->

# CREATE MESSAGE Statement \[T-SQL\] for Data Lake Relational Engine

Adds a user-defined message to the `SYSUSERMESSAGES` system table for use by `PRINT` and `RAISERROR` statements.



<a name="loioa61829d784f210158a99f4e03b39b150__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE MESSAGE <message-number>
... AS '<message-text>';
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61829d784f210158a99f4e03b39b150__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<message-number\>*

</b></dt>
<dd>

The message number of the message to add. The message number for a user-defined message must be 20000 or greater.



</dd><dt><b>

*<message\_text\>*

</b></dt>
<dd>

The text of the message to add. The maximum length is 255 bytes. `PRINT` and `RAISERROR` recognize placeholders in the message text to print out. A single message can contain up to 20 unique placeholders in any order. These placeholders are replaced with the formatted contents of any arguments that follow the message when the text of the message is sent to the client.

Placeholders are numbered to allow reordering of the arguments when translating a message to a language with a different grammatical structure. A placeholder for an argument appears as “%nn!” — a percent sign \(%\), followed by an integer from 1 to 20, followed by an exclamation mark \(!\) — where the integer represents the position of the argument in the argument list, “%1!” is the first argument, “%2!” is the second argument, and so on.



</dd>
</dl>



<a name="loioa61829d784f210158a99f4e03b39b150__IQ_Usage"/>

## Remarks

`CREATE MESSAGE` associates a message number with a message string. The message number can be used in `PRINT` and `RAISERROR` statements.



<a name="loioa61829d784f210158a99f4e03b39b150__IQ_Permissions"/>

## Privileges

Requires one of:

-   CREATE MESSAGE system privilege
-   CREATE ANY OBJECT system privilege

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa61829d784f210158a99f4e03b39b150__IQ_Side_Effects"/>

## Side Effects

Automatic commit



<a name="loioa61829d784f210158a99f4e03b39b150__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar

**Related Information**  


[DROP MESSAGE Statement for Data Lake Relational Engine](drop-message-statement-for-data-lake-relational-engine-e7d81ab.md "Removes a message from the database.")

[PRINT Statement \[T-SQL\] for Data Lake Relational Engine](print-statement-t-sql-for-data-lake-relational-engine-a6221e2.md "Displays a message on the message window of the database server.")

[RAISERROR Statement \[T-SQL\] for Data Lake Relational Engine](raiserror-statement-t-sql-for-data-lake-relational-engine-a6227d8.md "Allows user-defined errors to be signaled, and sends a message on the client.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

