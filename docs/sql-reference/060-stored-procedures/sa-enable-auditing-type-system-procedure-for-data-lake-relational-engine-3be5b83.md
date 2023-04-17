<!-- loio3be5b83e6c5f1014876dd3101b181f8a -->

# sa\_enable\_auditing\_type System Procedure for Data Lake Relational Engine

Specifies which events to include in auditing.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_enable_auditing_type( <types> )
```



<a name="loio3be5b83e6c5f1014876dd3101b181f8a__sa_enable_auditing_type_parm1"/>

## Parameters

  *<types\>* 
 :   Use this VARCHAR\(128\) parameter to specify a comma-delimited string containing one or more of the following values:

     all
     :   enables all types of auditing.

      connect
     :   enables auditing of both successful and failed connection attempts.

      connectFailed
     :   enables auditing of failed connection attempts.

      DDL
     :   enables auditing of DDL statements.

      options
     :   enables auditing of public options.

      permission
     :   enables auditing of permission checks and user checks.

      permissionDenied
     :   enables auditing of failed permission and user checks.

      triggers
     :   enables auditing of a trigger event.

      xp\_cmdshell
     :   enables auditing of xp\_cmdshell invocations.

  

<a name="loio3be5b83e6c5f1014876dd3101b181f8a__sa_enable_auditing_type_remarks1"/>

## Remarks

Use sa\_enable\_auditing\_type to specify which types of auditing to include. This system procedure adds the specified events to the current set of audit events. Use sa\_disable\_auditing\_type to remove events from the current set of audit events. These system procedures set the PUBLIC auditing\_options database option so the setting is permanent.

Set the PUBLIC auditing database option to On or Off to enable or disable auditing.

By default, all events are audited \(types='all'\). If you want a smaller set, use the sa\_disable\_auditing\_type system procedure to clear the events you aren’t interested in; or use the sa\_disable\_auditing\_type system procedure to clear all events and then use the sa\_enable\_auditing\_type system procedure to specify which types of auditing you want.

If the set of events is empty and you set the PUBLIC auditing database option to On, no auditing information is recorded. To re-establish auditing, you use the sa\_enable\_auditing\_type system procedure to specify which types of information you want to audit.

If you set the PUBLIC auditing database option to Off, then no auditing information is recorded.

Specify the location where events are logged with the audit\_log database option.



## Privileges

You need to have the EXECUTE privilege on the system procedure, as well as the SET ANY CUSTOMER SECURITY OPTION system privilege.



<a name="loio3be5b83e6c5f1014876dd3101b181f8a__sa_enable_auditing_type_sideefects1"/>

## Side Effects

None



The following example enables all auditing:

```
CALL sa_enable_auditing_type( 'all' );
```

The following example enables only DDL and triggers auditing:

```
CALL sa_disable_auditing_type( 'all' );
CALL sa_enable_auditing_type( 'DDL,triggers' );
```

The following example illustrates another way to enable only DDL and triggers auditing:

```
CALL sa_disable_auditing_type( 'all' );
CALL sa_enable_auditing_type( 'triggers' );
CALL sa_enable_auditing_type( 'DDL' );
```

**Related Information**  


[sa\_disable\_auditing\_type System Procedure for Data Lake Relational Engine](sa-disable-auditing-type-system-procedure-for-data-lake-relational-engine-3be5a6b.md "Disables auditing of specific events.")

[sa_enable_auditing_type System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/7bde72cc9e33425088c9b0d6a361d380.html "Specifies which events to include in auditing.") :arrow_upper_right:

