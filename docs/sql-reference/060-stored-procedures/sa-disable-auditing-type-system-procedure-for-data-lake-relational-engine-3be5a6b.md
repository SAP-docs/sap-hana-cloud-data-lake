<!-- loio3be5a6b16c5f1014ac1ca96bb9a4ce15 -->

# sa\_disable\_auditing\_type System Procedure for Data Lake Relational Engine

Disables auditing of specific events.



<a name="loio3be5a6b16c5f1014ac1ca96bb9a4ce15__section_rpg_3dw_f4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_disable_auditing_type( <types> )
```



<a name="loio3be5a6b16c5f1014ac1ca96bb9a4ce15__sa_disable_auditing_type_parm1"/>

## Parameters


<dl>
<dt><b>

*<types\>*

</b></dt>
<dd>

Use this VARCHAR\(128\) parameter to specify a comma-delimited string containing one or more of the following values:



</dd>
<dd>


<dl>
<dt><b>

all

</b></dt>
<dd>

Disables all types of auditing



</dd><dt><b>

authenticationProvider

</b></dt>
<dd>

Disables auditing of \{ALTER|CREATE|DROP\} \{JWT|LDAP|X509\} PROVIDER statements



</dd><dt><b>

backup

</b></dt>
<dd>

Disables auditing of \{BACKUP|RESTORE\} \{DATABASE|TABLE\} statements



</dd><dt><b>

certificate

</b></dt>
<dd>

Disables auditing of \{CREATE|DROP\} CERTIFICATE statements



</dd><dt><b>

connect

</b></dt>
<dd>

Disables auditing CONNECTION statements \(successful\)



</dd><dt><b>

connectFailed

</b></dt>
<dd>

Disables auditing of CONNECTION statements \(failed\)



</dd><dt><b>

database

</b></dt>
<dd>

Disables auditing of \{START|STOP\} DATABASE statements



</dd><dt><b>

delete

</b></dt>
<dd>

Disables auditing of DELETE and TRUNCATE statements



</dd><dt><b>

grant

</b></dt>
<dd>

Disables auditing of \{GRANT|REVOKE\} ANY statements



</dd><dt><b>

insert

</b></dt>
<dd>

Disables auditing of INSERT statements



</dd><dt><b>

load

</b></dt>
<dd>

Disables auditing of LOAD and UNLOAD statements



</dd><dt><b>

loginPolicy

</b></dt>
<dd>

Disables auditing when a user is locked out in accordance with their login policy \(because of failed logins or an expired password\)



</dd><dt><b>

loginPolicyDLL

</b></dt>
<dd>

Disables auditing of \{CREATE|ALTER|DROP\} LOGIN POLICY



</dd><dt><b>

options

</b></dt>
<dd>

Disables auditing of events that set any public option



</dd><dt><b>

otherDDL

</b></dt>
<dd>

Disables auditing of any DDLs not covered by other SYS\_Audit events for specific DDLs



</dd><dt><b>

procedure

</b></dt>
<dd>

Disables auditing of calls to procedures. The statements inside the procedure aren't audited unless you enable the related auditing type \(such as 'insert' or 'select'\).



</dd><dt><b>

select

</b></dt>
<dd>

Disables auditing of any SELECT that is directly executed, or directly executed within a procedure or function



</dd><dt><b>

setUser

</b></dt>
<dd>

Disables auditing of SETUSER statements



</dd><dt><b>

string

</b></dt>
<dd>

Disables auditing of comments added by sa\_audit\_string



</dd><dt><b>

triggers

</b></dt>
<dd>

Disables auditing of the start and end of a trigger



</dd><dt><b>

update

</b></dt>
<dd>

Disables auditing of UPDATE statements



</dd><dt><b>

user

</b></dt>
<dd>

Disables auditing of \{ALTER|CREATE|DROP\} \{USER|ROLE\} statements



</dd>
</dl>



</dd>
</dl>



<a name="loio3be5a6b16c5f1014ac1ca96bb9a4ce15__sa_disable_auditing_type_result1"/>

## Result Set

None



<a name="loio3be5a6b16c5f1014ac1ca96bb9a4ce15__sa_disable_auditing_type_remarks1"/>

## Remarks

Use sa\_disable\_auditing\_type to specify which types of auditing to exclude. This system procedure removes the specified events from the current set of audit events. Use sa\_enable\_auditing\_type to add events to the current set of audit events. These system procedures set the PUBLIC auditing\_options database option so the setting is permanent.

Set the PUBLIC auditing database option to On or Off to enable or disable auditing.

By default, all events are audited \(types='all'\). If you want a smaller set, use the sa\_disable\_auditing\_type system procedure to clear the events you aren’t interested in; or use the sa\_disable\_auditing\_type system procedure to clear all events and then use the sa\_enable\_auditing\_type system procedure to specify which types of auditing you want.

If the set of events is empty and you set the PUBLIC auditing database option to On, no auditing information is recorded. To re-establish auditing, you use the sa\_enable\_auditing\_type system procedure to specify which types of information you want to audit.

If you set the PUBLIC auditing database option to Off, then no auditing information is recorded.

Specify the location where events are logged with the audit\_log database option.



<a name="loio3be5a6b16c5f1014ac1ca96bb9a4ce15__sa_disable_auditing_type_priv1"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on the procedure
-   SET ANY CUSTOMER SECURITY OPTION system privilege
-   MANAGE AUDITING system privilege



<a name="loio3be5a6b16c5f1014ac1ca96bb9a4ce15__sa_disable_auditing_type_sideefects1"/>

## Side Effects

None



<a name="loio3be5a6b16c5f1014ac1ca96bb9a4ce15__sa_disable_auditing_type_example1"/>

## Examples

This example uses the sa\_disable\_auditing\_type system procedure to disable all auditing:

```
CALL sa_disable_auditing_type( 'all' );
```

This example enables only `insert` and `select` auditing:

```
CALL sa_disable_auditing_type( 'all' );
CALL sa_enable_auditing_type( 'insert,select' );
```

This example enables all auditing except for `insert` and `select` auditing:

```
CALL sa_enable_auditing_type( 'all' );
CALL sa_disable_auditing_type( 'insert,select' );
```

**Related Information**  


[sa\_enable\_auditing\_type System Procedure for Data Lake Relational Engine](sa-enable-auditing-type-system-procedure-for-data-lake-relational-engine-3be5b83.md "Specifies which events to include in auditing.")

[sa_disable_auditing_type System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/fd63ea1f8fb64064aee60207c5efbecb.html "Disables auditing of specific events.") :arrow_upper_right:

