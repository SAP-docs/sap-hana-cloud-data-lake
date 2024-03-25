<!-- loio056ee2c16cd548e3a811170533f684e7 -->

# ALTER PSE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Modifies an existing personal security environment \(PSE\).



<a name="loio056ee2c16cd548e3a811170533f684e7__section_egm_jff_2zb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
ALTER PSE <pse-name> 
   { <certificate-clause>
   | <set-own-certificate-clause>
   | <unset-own-certificate-clause> }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio056ee2c16cd548e3a811170533f684e7__section_ptt_5b3_fzb"/>

## Remarks

None



<a name="loio056ee2c16cd548e3a811170533f684e7__section_dls_tgb_fzb"/>

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



<a name="loio056ee2c16cd548e3a811170533f684e7__section_xxh_5gb_fzb"/>

## Side Effects

Automatic commit.



<a name="loio056ee2c16cd548e3a811170533f684e7__section_gcx_5gb_fzb"/>

## Examples

```
-- Setup for the following examples:
CREATE PSE MYPSE1;
CREATE CERTIFICATE Digicert FROM '-----BEGIN CERTIFICATE-----
-----END CERTIFICATE-----';
ALTER PSE mypse1 ADD CERTIFICATE Digicert;
```

> ### Note:  
> You can find details about root certificate updates on the DigiCert website at [https://knowledge.digicert.com/general-information/digicert-root-and-intermediate-ca-certificate-updates-2023](https://knowledge.digicert.com/general-information/digicert-root-and-intermediate-ca-certificate-updates-2023). Also see SAP Note [3397584](https://me.sap.com/notes/3397584), SAP Note [3327214](https://me.sap.com/notes/3327214) and SAP Note [3399572](https://me.sap.com/notes/3399572).

This example adds an own certificate to an the existing PSE mypse1. It also sets the private key, the own certificate, and its full chain.

```
ALTER PSE MYPSE SET OWN CERTIFICATE '-----BEGIN PRIVATE KEY-----
...-----END PRIVATE KEY-----
-----BEGIN CERTIFICATE-----
...-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
...-----END CERTIFICATE-----';
```

This example removes the private key, the own certificate, and its full chain from the PSE named mypse1.

```
ALTER PSE mypse1 UNSET OWN CERTIFICATE;
```

This example removes the certificate named DIGICERT from the PSE named mypse1.

```
ALTER PSE mypse1 DROP CERTIFICATE Digicert;
```

**Related Information**  


[CREATE PSE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-pse-statement-for-data-lake-relational-engine-sap-hana-db-managed-bc673db.md "Create a personal security environment (PSE).")

[DROP PSE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-pse-statement-for-data-lake-relational-engine-sap-hana-db-managed-daf65f6.md "Removes a personal security environment (PSE) from the database.")

[ALTER PSE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/53742a28df0f40deb5cd7a9784fc1a55.html "Modifies an existing personal security environment (PSE).") :arrow_upper_right:

