<!-- loio3be5a6b16c5f1014ac1ca96bb9a4ce15 -->

# sa\_disable\_auditing\_type System Procedure for Data Lake Relational Engine

Disables auditing of specific events.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
dbo.sa_disable_auditing_type( <types> )
```



<a name="loio3be5a6b16c5f1014ac1ca96bb9a4ce15__sa_disable_auditing_type_parm1"/>

## Parameters

  *<types\>* 
 :   Use this VARCHAR\(128\) parameter to specify a comma-delimited string containing one or more of the following values:

     all
     :   disables all types of auditing.

      connect
     :   disables auditing of both successful and failed connection attempts.

      connectFailed
     :   disables auditing of failed connection attempts.

      DDL
     :   disables auditing of DDL statements.

      options
     :   disables auditing of public options.

      permission
     :   disables auditing of permission checks and user checks.

      permissionDenied
     :   disables auditing of failed permission and user checks.

      triggers
     :   disables auditing in response to trigger events.

      xp\_cmdshell
     :   disables auditing for xp\_cmdshell.

  

<a name="loio3be5a6b16c5f1014ac1ca96bb9a4ce15__sa_disable_auditing_type_remarks1"/>

## Remarks

Use dbo.sa\_disable\_auditing\_type to specify which types of auditing to exclude. This system procedure removes the specified events from the current set of audit events. Use dbo.sa\_enable\_auditing\_type to add events to the current set of audit events. These system procedures set the PUBLIC auditing\_options database option so the setting is permanent.

Set the PUBLIC auditing database option to On or Off to enable or disable auditing.

By default, all events are audited \(types='all'\). If you want a smaller set, use the dbo.sa\_disable\_auditing\_type system procedure to clear the events you aren’t interested in; or use the dbo.sa\_disable\_auditing\_type system procedure to clear all events and then use the dbo.sa\_enable\_auditing\_type system procedure to specify which types of auditing you want.

If the set of events is empty and you set the PUBLIC auditing database option to On, no auditing information is recorded. To re-establish auditing, you use the dbo.sa\_enable\_auditing\_type system procedure to specify which types of information you want to audit.

If you set the PUBLIC auditing database option to Off, then no auditing information is recorded.

Specify the location where events are logged with the audit\_log database option.



## Privileges

You need to have the EXECUTE privilege on the system procedure, as well as the SET ANY CUSTOMER SECURITY OPTION system privilege.



<a name="loio3be5a6b16c5f1014ac1ca96bb9a4ce15__sa_disable_auditing_type_sideefects1"/>

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


[sa\_enable\_auditing\_type System Procedure for Data Lake Relational Engine](sa-enable-auditing-type-system-procedure-for-data-lake-relational-engine-3be5b83.md "Specifies which events to include in auditing.")

[sa_disable_auditing_type System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/fd63ea1f8fb64064aee60207c5efbecb.html "Disables auditing of specific events.") :arrow_upper_right:

