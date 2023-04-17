<!-- loio5ba698c94d6549e0acee64463a108773 -->

# PROGRESS\_MESSAGES Option for Data Lake Relational Engine

Controls whether progress messages are sent from the database server to the client.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio5ba698c94d6549e0acee64463a108773__section_zx3_g24_hrb"/>

## Syntax

```
PROGRESS_MESSAGES = <value>
```



<a name="loio5ba698c94d6549e0acee64463a108773__iq_refso_866"/>

## Allowed Values

OFF, RAW, FORMATTED



<a name="loio5ba698c94d6549e0acee64463a108773__iq_refso_867"/>

## Default

OFF



<a name="loio5ba698c94d6549e0acee64463a108773__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio5ba698c94d6549e0acee64463a108773__iq_refso_868"/>

## Scope


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

PUBLIC Role



</th>
<th valign="top">

For Current User



</th>
<th valign="top">

For Other Users



</th>
</tr>
<tr>
<td valign="top">

Allowed to set permanently?



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes \(current connection only\)



</td>
<td valign="top">

No



</td>
</tr>
</table>



## Remarks


<table>
<tr>
<th valign="top">

Value



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

OFF



</td>
<td valign="top">

Progress messages are not sent to the client.



</td>
</tr>
<tr>
<td valign="top">

RAW



</td>
<td valign="top">

Uses the following format progress messages:

```
43;9728;22230;pages;5025;6138
```

Raw progress messages have six fields separated by semicolons that are defined as follows:

-   Field 1 – percentage of statement executed.t
-   Field 2 – number of completed pages, rows, or bytes.
-   Field 3 – number of pages, rows, or bytes to be processed.
-   Field 4 – what is being processed: pages, rows, or bytes.
-   Field 5 – current elapsed time displayed in milliseconds.
-   Field 6 – estimated time in milliseconds remaining to complete the execution of the statement



</td>
</tr>
<tr>
<td valign="top">

FORMATTED



</td>
<td valign="top">

When selected, progress messages use the following format:

```
43% (9728 of 22230 pages) complete after 00:00:05; estimated 00:00:06
remaining
```



</td>
</tr>
</table>

Formatted progress messages are localized, and the time format is HH:MM:SS. Units less than 100 KB are displayed in bytes, units less than 100 MB are displayed in KB, and units greater than 100 MB are displayed in MB.

Progress messages are sent at intervals that are 5% of the total estimated duration of the statement. Typically, the estimate is completed and the first progress message is sent within 10 seconds. Additional progress messages are sent in intervals of 30 seconds to 5 minutes. If the percentage complete is identical to the value sent in a previous message, an updated progress message is not sent until more than 5 minutes have elapsed since the last message was sent. Progress messages are not sent for statements that take less than 30 seconds to execute.

Estimates are recalculated continually; the accuracy of the remaining time estimate increases as the operation progresses. During events such as backups, the total number of pages may be adjusted during statement execution, so the percent complete and remaining time estimates change. With statements such as BACKUP...WITH CHECKPOINT COPY or UNLOAD SELECT the total number of affected pages or rows is unknown and it is possible for the percentage complete value to be greater than 100%. As a result, the estimated remaining time cannot be calculated and it is not included in the progress message.

The following statements and procedures support progress messages on the IQ catalog row-store portion:

-   LOAD TABLE \(USING FILE and USING CLIENT FILE only\)
-   MESSAGE
-   UNLOAD \(all types\)
-   sa\_table\_page\_usage system procedure

You can set the PROGRESS\_MESSAGES option when you are connected to the utility database using the SET OPTION statement.

You can also set the PROGRESS\_MESSAGES option in Interactive SQL by clicking *Tools* \> *Options* \> *Data Lake Relational Engine* \> *Execution*, and then clicking *Show progress messages*. When Show Progress Messages is enabled, the progress\_messages option is set to Formatted.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

