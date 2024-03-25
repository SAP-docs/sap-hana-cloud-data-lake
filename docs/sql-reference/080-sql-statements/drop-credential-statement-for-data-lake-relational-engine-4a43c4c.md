<!-- loio4a43c4c30466458ba7c9c80ec44f6bdc -->

# DROP CREDENTIAL Statement for Data Lake Relational Engine

Drops an existing component-specific or application-specific credential.



<a name="loio4a43c4c30466458ba7c9c80ec44f6bdc__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP CREDENTIAL FOR [ USER <user-name> ] COMPONENT <component-id> 
   PURPOSE <purpose-def> TYPE <type-def>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio4a43c4c30466458ba7c9c80ec44f6bdc__drop_credential_param1"/>

## Parameters


<dl>
<dt><b>

*<user-name\>*

</b></dt>
<dd>

Specifies the owner of the credential being dropped.



</dd><dt><b>

*<component-id\>*

</b></dt>
<dd>

Specifies a component of the credential being dropped.



</dd><dt><b>

*<purpose-def\>*

</b></dt>
<dd>

Specifies the application-specific or component-specific purpose string of the credential being dropped.



</dd><dt><b>

*<type-def\>*

</b></dt>
<dd>

Specifies a component specific type of the credential being dropped.



</dd>
</dl>



<a name="loio4a43c4c30466458ba7c9c80ec44f6bdc__drop_credential_remarks1"/>

## Remarks

When dropping a credential, the *<user-name\>*, *<component-id\>*, *<purpose-def\>*, and *<type-def\>* combination specified must match exactly. Do not specify a user when dropping the credential, if no user was specified during creation of the credential.



<a name="loio4a43c4c30466458ba7c9c80ec44f6bdc__drop_credential_priv1"/>

## Privileges



### 

Requires one of the following:

-   You are the credential user.
-   MANAGE CREDENTIAL system privilege

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loio4a43c4c30466458ba7c9c80ec44f6bdc__drop_credential_side_effect1"/>

## Side Effects

Automatic commit



<a name="loio4a43c4c30466458ba7c9c80ec44f6bdc__drop_credential_examples1"/>

## Examples

This example drops the credential where *<user-name\>* is user1 *<component-id\>* is SAPHDLRELOADUNLOAD, *<purpose-def\>* is AccessHDLFS and *<type-def\>* is X509.

```
DROP CREDENTIAL FOR USER user1 COMPONENT 'SAPHDLRELOADUNLOAD' PURPOSE 'AccessHDLFS' TYPE 'X509';
```

**Related Information**  


[CREATE CREDENTIAL Statement for Data Lake Relational Engine](create-credential-statement-for-data-lake-relational-engine-642b497.md "Creates a component-specific or application-specific credential.")

[DROP CREDENTIAL Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/b1503e6de40c4360b44486c19f7478c2.html "Drops an existing component-specific or application-specific credential.") :arrow_upper_right:

