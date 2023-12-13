<!-- loio91397ea648a746b6ab4cad01476982e5 -->

# DROP AUDIT POLICY Statement for SAP HANA Database

Drops an audit policy.



<a name="loio91397ea648a746b6ab4cad01476982e5__sql_drop_audit_policy_1sql_drop_audit_policy_syntax"/>

## Syntax

```
DROP AUDIT POLICY <policy_name>
```



<a name="loio91397ea648a746b6ab4cad01476982e5__sql_drop_audit_policy_1sql_drop_audit_policy_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<policy\_name\>*

</b></dt>
<dd>

Specifies the name of the audit policy to be dropped.

```
<policy_name> ::= <identifier>
```

*<policy\_name\>* must specify an existing audit policy.



</dd>
</dl>



<a name="loio91397ea648a746b6ab4cad01476982e5__sql_drop_audit_policy_1sql_drop_audit_policy_description"/>

## Description

Even if an audit policy is dropped, the audit action specified in the dropped audit policy can be audited further. This happens if another audit policy is enabled that specifies the dropped audit action.

To temporarily stop auditing an audit policy, disable it.

Since there is no automatic deletion of audit log entries for deleted policies, audit log entries created by such a policy need to be cleaned up manually.



<a name="loio91397ea648a746b6ab4cad01476982e5__section_snl_sp5_qbb"/>

## Permissions

To drop an audit policy, you must have the AUDIT ADMIN system privilege.



<a name="loio91397ea648a746b6ab4cad01476982e5__sql_drop_audit_policy_1sql_drop_audit_policy_examples"/>

## Example

Create the priv\_audit audit policy.

```
CREATE AUDIT POLICY priv_audit AUDITING SUCCESSFUL GRANT PRIVILEGE, REVOKE PRIVILEGE, GRANT ROLE, REVOKE ROLE LEVEL CRITICAL;
```

Drop the priv\_audit audit policy.

```
DROP AUDIT POLICY priv_audit;
```

