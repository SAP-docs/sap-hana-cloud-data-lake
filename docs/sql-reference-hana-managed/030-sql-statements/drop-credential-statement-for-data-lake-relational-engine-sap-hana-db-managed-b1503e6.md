<!-- loiob1503e6de40c4360b44486c19f7478c2 -->

# DROP CREDENTIAL Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Drops an existing component-specific or application-specific credential.



<a name="loiob1503e6de40c4360b44486c19f7478c2__section_egm_jff_2zb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
DROP CREDENTIAL FOR [ USER <user-name> ] COMPONENT <component-id> 
   PURPOSE <purpose-def> TYPE <type-def>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiob1503e6de40c4360b44486c19f7478c2__section_fmy_phf_2zb"/>

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



<a name="loiob1503e6de40c4360b44486c19f7478c2__section_wgx_qhf_2zb"/>

## Remarks

When dropping a credential, the *<user-name\>*, *<component-id\>*, *<purpose-def\>*, and *<type-def\>* combination specified must match exactly. Do not specify a user when dropping the credential, if no user was specified during creation of the credential.



<a name="loiob1503e6de40c4360b44486c19f7478c2__section_tj5_rhf_2zb"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user.:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd>
</dl>



<a name="loiob1503e6de40c4360b44486c19f7478c2__section_opf_whf_2zb"/>

## Side Effects

Automatic commit



<a name="loiob1503e6de40c4360b44486c19f7478c2__section_d1z_shf_2zb"/>

## Examples

This example drops the credential where *<user-name\>* is user1 *<component-id\>* is SAPHDLRELOADUNLOAD, *<purpose-def\>* is AccessHDLFS and *<type-def\>* is X509.

```
DROP CREDENTIAL FOR USER user1 COMPONENT 'SAPHDLRELOADUNLOAD' PURPOSE 'AccessHDLFS' TYPE 'X509';
```

**Related Information**  


[CREATE CREDENTIAL Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-credential-statement-for-data-lake-relational-engine-sap-hana-db-managed-da4e344.md "Creates a component-specific or application-specific credential.")

[DROP CREDENTIAL Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/4a43c4c30466458ba7c9c80ec44f6bdc.html "Drops an existing component-specific or application-specific credential.") :arrow_upper_right:

