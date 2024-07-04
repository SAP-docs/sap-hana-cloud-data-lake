<!-- loioda4e344cbb6847d09833bbf3cdc3c441 -->

# CREATE CREDENTIAL Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Creates a component-specific or application-specific credential.



<a name="loioda4e344cbb6847d09833bbf3cdc3c441__section_wgg_skf_2zb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
CREATE CREDENTIAL FOR COMPONENT '<component-id>' 
   PURPOSE '<purpose-def>' TYPE '<type-def>' [ PSE '<pse-name>' ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioda4e344cbb6847d09833bbf3cdc3c441__section_gmm_ncb_fzb"/>

## Parameters


<dl>
<dt><b>

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



<a name="loioda4e344cbb6847d09833bbf3cdc3c441__section_gwc_4cb_fzb"/>

## Remarks

The specified user\_name, component\_id, purpose\_def, and type\_def of the credential must be unique. If multiple credentials are created, some with a user name specified and some without, then cascading logic checks first by user and then by all other users when using the credential. For example, if a credential exists that is defined for userA \(credential 1\) and another credential exists that had no user name defined \(credential 2\), userA would use credential 1 and userB, userC... would use creadential2.



<a name="loioda4e344cbb6847d09833bbf3cdc3c441__section_pf4_4cb_fzb"/>

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



<a name="loioda4e344cbb6847d09833bbf3cdc3c441__section_hnq_3db_fzb"/>

## Side Effects

Automatic commit.



<a name="loioda4e344cbb6847d09833bbf3cdc3c441__section_p2d_pcb_fzb"/>

## Examples

This example creates a credential that is associated with PSE mypse1.

```
CREATE CREDENTIAL FOR COMPONENT 'SAPHDLRELOADUNLOAD' PURPOSE 'AccessHDLFS' TYPE 'X509' PSE 'mypse1';
```

**Related Information**  


[DROP CREDENTIAL Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-credential-statement-for-data-lake-relational-engine-sap-hana-db-managed-b1503e6.md "Drops an existing component-specific or application-specific credential.")

[SYSCREDENTIAL System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../070-system-views/syscredential-system-view-for-data-lake-relational-engine-sap-hana-db-managed-02e7127.md "Provides information about credentials for users and components.")

[Secure Internal Credential Store in Data Lake Relational Engine](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_3_QRC/en-US/2448dedf04dc4606bb6983ce99f1e163.html "The credentials required by data lake Relational Engine for outbound connections are securely stored in a database-internal credential store.") :arrow_upper_right:

[CREATE CREDENTIAL Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/642b4974ed3d4f0d81f0ce6faaea50fe.html "Creates a component-specific or application-specific credential.") :arrow_upper_right:

