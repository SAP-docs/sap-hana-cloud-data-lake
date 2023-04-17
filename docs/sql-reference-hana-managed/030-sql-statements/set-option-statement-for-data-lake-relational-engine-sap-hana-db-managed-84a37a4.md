<!-- loio84a37a4b73ff4ba1ae53aad6b4c94803 -->

# SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).



```
SET [ EXISTING ] [ TEMPORARY ] OPTION
   … [ { [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <user_id> (varname] | PUBLIC }.][/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <option-name> (varname] = [ [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <option-value> (varname] ]
```



<a name="loio84a37a4b73ff4ba1ae53aad6b4c94803__section_uvj_mrw_brb"/>

## Parameters

 *<option-value\>*
 :   A host-variable \(indicator allowed\), string, identifier, or number. The maximum length of *<option-value\>* when set to a string is 127 bytes.

    If *<option-value\>* is omitted, the specified option setting is deleted from the database. If it was a personal option setting, the value used reverts to the PUBLIC setting.

    > ### Note:  
    > For all database options that accept integer values, data lake Relational Engine truncates any decimal *<option-value\>* setting to an integer value. For example, the value 3.8 is truncated to 3.

  EXISTING
 :   Option values cannot be set for an individual user ID unless there is already a PUBLIC user ID setting for that option.

  TEMPORARY
 :   Changes the duration that the change takes effect. Without the TEMPORARY clause, an option change is permanent: it does not change until it is explicitly changed using SET OPTION statement.

    When the TEMPORARY clause is applied using an individual user ID, the new option value is in effect as long as that user is logged in to the database.

    When the TEMPORARY clause is used with the PUBLIC user ID, the change is in place for as long as the database is running. When the database is shut down, TEMPORARY options for the PUBLIC user ID revert to their permanent value.

    If a TEMPORARY option is deleted, the option setting reverts to the permanent setting.

 

<a name="loio84a37a4b73ff4ba1ae53aad6b4c94803__section_erw_mrw_brb"/>

## Remarks

The classes of options are:

-   General database options
-   Transact-SQL compatibility database options

Specifying either a user ID or the PUBLIC user ID determines whether the option is set for an individual user, a role represented by *<user\_id\>*, or the PUBLIC user ID \(the role to which all users are a member\). If the option applies to a role ID, option settings are not inherited by members of the role — the change is applied only to the role ID. If no role is specified, the option change is applied to the currently logged-in user ID that issued the SET OPTION statement. For example, this statement applies an option change to the PUBLIC user ID:

```
SET OPTION Public.login_mode = standard
```

In Embedded SQL, only database options can be set temporarily.

Changing the value of an option for the PUBLIC user ID sets the value of the option for any user that has not set its own value. Option values cannot be set for an individual user ID unless there is already a PUBLIC user ID setting for that option.

Temporarily setting an option for the PUBLIC user ID, as opposed to setting the value of the option permanently, offers a security advantage. For example, when the LOGIN\_MODE option is enabled, the database relies on the login security of the system on which it is running. Enabling the option temporarily means a database relying on the security of a Windows domain is not compromised if the database is shut down and copied to a local machine. In that case, the temporary enabling of LOGIN\_MODE reverts to its permanent value, which might be Standard, a mode in which integrated logins are not permitted.

> ### Caution:  
> Changing option settings while fetching rows from a cursor is not supported, as it can lead to unpredictable behavior. For example, changing the DATE\_FORMAT setting while fetching from a cursor returns different date formats among the rows in the result set. Do not change option settings while fetching rows.



<a name="loio84a37a4b73ff4ba1ae53aad6b4c94803__section_ahv_kyy_wwb"/>

## Privileges



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio84a37a4b73ff4ba1ae53aad6b4c94803__section_nsb_4rw_brb"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar.



<a name="loio84a37a4b73ff4ba1ae53aad6b4c94803__section_nmp_4rw_brb"/>

## Examples

-   The following example sets the DATE\_FORMAT option:

    ```
    SET OPTION public.date_format = 'Mmm dd yyyy'
    ```

-   The following example sest the WAIT\_FOR\_COMMIT option to on:

    ```
    SET OPTION wait_for_commit = 'on'
    ```

-   The following example embeddes SQL examples:

    ```
    EXEC SQL SET OPTION :user.:option_name = :value;
    EXEC SQL SET TEMPORARY OPTION Date_format = 'mm/dd/yyyy';
    ```


**Related Information**  


[Database Options in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../040-database-options/database-options-in-data-lake-relational-engine-sap-hana-db-managed-8d17dee.md "Database options customize and modify database behavior.")

[SET OPTION Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a625da7584f21015a300a0dd2457eb57.html "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.") :arrow_upper_right:

