<!-- loio3be5b83e6c5f1014876dd3101b181f8a -->

# sa\_enable\_auditing\_type System Procedure for Data Lake Relational Engine

Specifies which events to include in auditing.



<a name="loio3be5b83e6c5f1014876dd3101b181f8a__section_rpg_3dw_f4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_enable_auditing_type( <types> )
```



<a name="loio3be5b83e6c5f1014876dd3101b181f8a__sa_enable_auditing_type_parm1"/>

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

Enables all types of auditing



</dd><dt><b>

authenticationProvider

</b></dt>
<dd>

Enables auditing of \{ALTER|CREATE|DROP\} \{JWT|LDAP|X509\} PROVIDER statements



</dd><dt><b>

backup

</b></dt>
<dd>

Enables auditing of \{BACKUP|RESTORE\} \{DATABASE|TABLE\} statements



</dd><dt><b>

certificate

</b></dt>
<dd>

Enables auditing of \{CREATE|DROP\} CERTIFICATE statements



</dd><dt><b>

connect

</b></dt>
<dd>

Enables auditing CONNECTION statements \(successful\)



</dd><dt><b>

connectFailed

</b></dt>
<dd>

Enables auditing of CONNECTION statements \(failed\)



</dd><dt><b>

database

</b></dt>
<dd>

Enables auditing of \{START|STOP\} DATABASE statements



</dd><dt><b>

delete

</b></dt>
<dd>

Enables auditing of DELETE and TRUNCATE statements



</dd><dt><b>

grant

</b></dt>
<dd>

Enables auditing of \{GRANT|REVOKE\} ANY statements



</dd><dt><b>

insert

</b></dt>
<dd>

Enables auditing of INSERT statements



</dd><dt><b>

load

</b></dt>
<dd>

Enables auditing of LOAD and UNLOAD statements



</dd><dt><b>

loginPolicy

</b></dt>
<dd>

Enables auditing when a user is locked out in accordance with their login policy \(because of failed logins or an expired password\)



</dd><dt><b>

loginPolicyDDL

</b></dt>
<dd>

Enables auditing of \{CREATE|ALTER|DROP\} LOGIN POLICY



</dd><dt><b>

options

</b></dt>
<dd>

Enables auditing of events that set any public option



</dd><dt><b>

otherDDL

</b></dt>
<dd>

Enables auditing of any DDLs not covered by other SYS\_Audit events for specific DDLs



</dd><dt><b>

procedure

</b></dt>
<dd>

Enables auditing of calls to procedures. The statements inside the procedure aren't audited unless you enable the related auditing type \(such as 'insert' or 'select'\).



</dd><dt><b>

select

</b></dt>
<dd>

Enables auditing of any SELECT that is directly executed, or directly executed within a procedure or function



</dd><dt><b>

setUser

</b></dt>
<dd>

Enables auditing of SETUSER statements



</dd><dt><b>

string

</b></dt>
<dd>

Enables auditing of comments added by sa\_audit\_string



</dd><dt><b>

triggers

</b></dt>
<dd>

Enables auditing of the start and end of a trigger



</dd><dt><b>

update

</b></dt>
<dd>

Audits all UPDATE statements



</dd><dt><b>

user

</b></dt>
<dd>

Enables auditing of \{ALTER|CREATE|DROP\} \{USER|ROLE\} statements



</dd>
</dl>



</dd>
</dl>



<a name="loio3be5b83e6c5f1014876dd3101b181f8a__sa_enable_auditing_type_result1"/>

## Result Set

None



<a name="loio3be5b83e6c5f1014876dd3101b181f8a__sa_enable_auditing_type_remarks1"/>

## Remarks

Use sa\_enable\_auditing\_type to specify which types of auditing to include. This system procedure adds the specified events to the current set of audit events. Use sa\_disable\_auditing\_type to remove events from the current set of audit events. These system procedures set the PUBLIC auditing\_options database option so the setting is permanent.

Set the PUBLIC auditing database option to On or Off to enable or disable auditing.

By default, all events are audited \(types='all'\). If you want a smaller set, use the sa\_disable\_auditing\_type system procedure to clear the events you're not interested in; or use the sa\_disable\_auditing\_type system procedure to clear all events and then use the sa\_enable\_auditing\_type system procedure to specify which types of auditing you want.

If the set of events is empty and you set the PUBLIC auditing database option to On, no auditing information is recorded. To re-establish auditing, you use the sa\_enable\_auditing\_type system procedure to specify which types of information you want to audit.

If you set the PUBLIC auditing database option to Off, then no auditing information is recorded.

Specify the location where events are logged with the audit\_log database option.



<a name="loio3be5b83e6c5f1014876dd3101b181f8a__sa_enable_auditing_type_priv1"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on the procedure
-   SET ANY CUSTOMER SECURITY OPTION system privilege



<a name="loio3be5b83e6c5f1014876dd3101b181f8a__sa_enable_auditing_type_sideefects1"/>

## Side Effects

None



<a name="loio3be5b83e6c5f1014876dd3101b181f8a__sa_enable_auditing_type_examples1"/>

## Examples

This example uses the sa\_enable\_auditing\_type system procedure to enable all auditing:

```
CALL sa_enable_auditing_type( 'all' );
```

This example enables only DDL and triggers auditing:

```
CALL sa_disable_auditing_type( 'all' );
CALL sa_enable_auditing_type( 'DDL,triggers' );
```

This example illustrates another way to enable only DDL and triggers auditing:

```
CALL sa_disable_auditing_type( 'all' );
CALL sa_enable_auditing_type( 'triggers' );
CALL sa_enable_auditing_type( 'DDL' );
```

**Related Information**  


[sa\_disable\_auditing\_type System Procedure for Data Lake Relational Engine](sa-disable-auditing-type-system-procedure-for-data-lake-relational-engine-3be5a6b.md "Disables auditing of specific events.")

[sa_enable_auditing_type System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/7bde72cc9e33425088c9b0d6a361d380.html "Specifies which events to include in auditing.") :arrow_upper_right:

