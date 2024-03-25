<!-- loio642b4974ed3d4f0d81f0ce6faaea50fe -->

# CREATE CREDENTIAL Statement for Data Lake Relational Engine

Creates a component-specific or application-specific credential.



<a name="loio642b4974ed3d4f0d81f0ce6faaea50fe__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE CREDENTIAL FOR [ USER <user-name> ] COMPONENT '<component-id>' 
   PURPOSE '<purpose-def>' TYPE '<type-def>' [ PSE '<pse-name>' ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio642b4974ed3d4f0d81f0ce6faaea50fe__create_credential_param1"/>

## Parameters


<dl>
<dt><b>

*<user-name\>*

</b></dt>
<dd>

Specifies the only user who can use the credential. If a user is not specified, then every user of the current instance uses the same credential when the following conditions are true:

-   The user is using the specified component.
-   The component has access to the remote system specified by the PURPOSE parameter.



</dd><dt><b>

*<component-id\>*

</b></dt>
<dd>

Specifies a component that uses the credential.

```
<component-id> ::= SAPHDLRELOADUNLOAD
```



</dd><dt><b>

*<purpose-def\>*

</b></dt>
<dd>

A user provided string literal that specifies the application-specific or component-specific purpose string.

```
<purpose-def> ::= <string>
```



</dd><dt><b>

*<type-def\>*

</b></dt>
<dd>

Specifies a component specific type.

```
<type-def> ::= X509
```



</dd><dt><b>

*<pse-name\>*

</b></dt>
<dd>

Specifies the PSE name associated with this credential. The current user must own the PSE to associate it with this credential.

```
<pse-name> ::= { <string> | <simple-identifier> }
```



</dd>
</dl>



<a name="loio642b4974ed3d4f0d81f0ce6faaea50fe__create_credential_remarks1"/>

## Remarks

The specified user\_name, component\_id, purpose\_def, and type\_def of the credential must be unique. If multiple credentials are created, some with a user name specified and some without, then cascading logic checks first by user and then by all other users when using the credential. For example, if a credential exists that is defined for userA \(credential 1\) and another credential exists that had no user name defined \(credential 2\), userA would use credential 1 and userB, userC... would use creadential2.



<a name="loio642b4974ed3d4f0d81f0ce6faaea50fe__create_credential_priv1"/>

## Privileges



### 

Requires the MANAGE CREDENTIAL system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loio642b4974ed3d4f0d81f0ce6faaea50fe__create_credential_side_effects"/>

## Side Effects

Automatic commit.



<a name="loio642b4974ed3d4f0d81f0ce6faaea50fe__create_credential_examples1"/>

## Examples

This example creates a credential that is used only by user1 and is associated with PSE mypse1.

```
CREATE CREDENTIAL FOR USER user1 COMPONENT 'SAPHDLRELOADUNLOAD' PURPOSE 'AccessHDLFS' TYPE 'X509' PSE 'mypse1';
```

This example creates a credential that is used by all users and is associated with PSE mypse1.

```
CREATE CREDENTIAL FOR COMPONENT 'SAPHDLRELOADUNLOAD' PURPOSE 'AccessHDLFS' TYPE 'X509' PSE 'mypse1';
```

**Related Information**  


[DROP CREDENTIAL Statement for Data Lake Relational Engine](drop-credential-statement-for-data-lake-relational-engine-4a43c4c.md "Drops an existing component-specific or application-specific credential.")

[SYSCREDENTIAL System View for Data Lake Relational Engine](../070-system-and-monitoring-views/syscredential-system-view-for-data-lake-relational-engine-958861c.md "Provides information about credentials for users and components.")

[Secure Internal Credential Store in Data Lake Relational Engine](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_1_QRC/en-US/2448dedf04dc4606bb6983ce99f1e163.html "The credentials required by data lake Relational Engine for outbound connections are securely stored in a database-internal credential store.") :arrow_upper_right:

[CREATE CREDENTIAL Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/da4e344cbb6847d09833bbf3cdc3c441.html "Creates a component-specific or application-specific credential.") :arrow_upper_right:

