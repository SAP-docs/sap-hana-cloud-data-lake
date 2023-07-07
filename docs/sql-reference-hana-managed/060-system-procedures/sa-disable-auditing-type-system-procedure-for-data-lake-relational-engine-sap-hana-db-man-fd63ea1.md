<!-- loiofd63ea1f8fb64064aee60207c5efbecb -->

# sa\_disable\_auditing\_type System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Disables auditing of specific events.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Running Procedures](remote-execute-usage-examples-for-running-procedures-3e7f86d.md) for more information.



```
dbo.sa_disable_auditing_type( <types> )
```



<a name="loiofd63ea1f8fb64064aee60207c5efbecb__section_uph_hw4_rrb"/>

## Parameters


<dl>
<dt><b>

 *<types\>* 

</b></dt>
<dd>

Use this VARCHAR\(128\) parameter to specify a comma-delimited string containing one or more of the following values:


<dl>
<dt><b>

all

</b></dt>
<dd>

disables all types of auditing.



</dd><dt><b>

connect

</b></dt>
<dd>

disables auditing of both successful and failed connection attempts.



</dd><dt><b>

connectFailed

</b></dt>
<dd>

disables auditing of failed connection attempts.



</dd><dt><b>

DDL

</b></dt>
<dd>

disables auditing of DDL statements.



</dd><dt><b>

options

</b></dt>
<dd>

disables auditing of public options.



</dd><dt><b>

permission

</b></dt>
<dd>

disables auditing of permission checks and user checks.



</dd><dt><b>

permissionDenied

</b></dt>
<dd>

disables auditing of failed permission and user checks.



</dd><dt><b>

triggers

</b></dt>
<dd>

disables auditing in response to trigger events.



</dd><dt><b>

xp\_cmdshell

</b></dt>
<dd>

disables auditing for xp\_cmdshell.



</dd>
</dl>



</dd>
</dl>



<a name="loiofd63ea1f8fb64064aee60207c5efbecb__section_fnv_hw4_rrb"/>

## Remarks

Use dbo.sa\_disable\_auditing\_type to specify which types of auditing to exclude. This system procedure removes the specified events from the current set of audit events. Use dbo.sa\_enable\_auditing\_type to add events to the current set of audit events. These system procedures set the PUBLIC auditing\_options database option so the setting is permanent.

Set the PUBLIC auditing database option to On or Off to enable or disable auditing.

By default, all events are audited \(types='all'\). If you want a smaller set, use the dbo.sa\_disable\_auditing\_type system procedure to clear the events you aren’t interested in; or use the dbo.sa\_disable\_auditing\_type system procedure to clear all events and then use the dbo.sa\_enable\_auditing\_type system procedure to specify which types of auditing you want.

If the set of events is empty and you set the PUBLIC auditing database option to On, no auditing information is recorded. To re-establish auditing, you use the dbo.sa\_enable\_auditing\_type system procedure to specify which types of information you want to audit.

If you set the PUBLIC auditing database option to Off, then no auditing information is recorded.

Specify the location where events are logged with the audit\_log database option.



## Privileges

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loiofd63ea1f8fb64064aee60207c5efbecb__section_yyt_cw4_rrb"/>

## Side Effects

None



The following example disables all auditing:

```
CALL dbo.sa_disable_auditing_type( 'all' );
```

The following example enables only DDL and triggers auditing:

```
CALL dbo.sa_disable_auditing_type( 'all' );
CALL dbo.sa_enable_auditing_type( 'DDL,triggers' );
```

The following example enables all auditing except for DDL and options auditing:

```
CALL dbo.sa_enable_auditing_type( 'all' );
CALL dbo.sa_disable_auditing_type( 'DDL,options' );
```

**Related Information**  


[sa\_enable\_auditing\_type System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sa-enable-auditing-type-system-procedure-for-data-lake-relational-engine-sap-hana-db-mana-7bde72c.md "Specifies which events to include in auditing.")

[sa_disable_auditing_type System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/3be5a6b16c5f1014ac1ca96bb9a4ce15.html "Disables auditing of specific events.") :arrow_upper_right:

