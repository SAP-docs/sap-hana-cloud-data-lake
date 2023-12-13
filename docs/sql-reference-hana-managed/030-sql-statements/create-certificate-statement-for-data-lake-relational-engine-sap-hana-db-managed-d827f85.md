<!-- loiod827f8589599403c94bd8700114c9e46 -->

# CREATE CERTIFICATE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Adds or replaces a certificate in the database using the given file or string.



<a name="loiod827f8589599403c94bd8700114c9e46__section_egm_jff_2zb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure.



```
CREATE [ OR REPLACE ] CERTIFICATE <certificate-name>
   [ PURPOSE { JWT | X509 } FOR PROVIDER <provider_name> ]
   FROM { <certificate-string> | <variable-name> }
;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiod827f8589599403c94bd8700114c9e46__section_m33_1c3_fzb"/>

## Parameters


<dl class="glossary">
<dt><b>

PURPOSE

</b></dt>
<dd>

Specifies the provider of the purpose for the certificate.



</dd><dt><b>

FROM

</b></dt>
<dd>

Specifies a string or file containing a certificate.



</dd>
</dl>



<a name="loiod827f8589599403c94bd8700114c9e46__section_i3l_bc3_fzb"/>

## Remarks

The string or file should contain either a binary DER-format certificate or a text PEM-format certificate. DER-format certificates are converted and stored as PEM certificates.

Certificates that are stored in the database can be used by web service procedures and functions that make secure HTTPS connections to a web server. Certificates with a specified PURPOSE can be used for user authentication.

The certificate is validated at login time, not when the certificate is created.

Use the SYSCERTIFICATE system view to display a list of certificates

The CREATE CERTIFICATE statement is not used to create an actual certificate. Use the Certificate Creation utility \(createcert\) to do this.



<a name="loiod827f8589599403c94bd8700114c9e46__section_vj1_cc3_fzb"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd>
</dl>



<a name="loiod827f8589599403c94bd8700114c9e46__section_ezr_zdb_fzb"/>

## Side Effects

Automatic commit.



<a name="loiod827f8589599403c94bd8700114c9e46__section_tfd_12b_fzb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



<a name="loiod827f8589599403c94bd8700114c9e46__section_k5r_12b_fzb"/>

## Example

This example creates a certificate with a JWT purpose.

```
CREATE CERTIFICATE my_cert1
PURPOSE JWT FOR PROVIDER my_jwt_provider
FROM '-----BEGIN CERTIFICATE-----
...-----END CERTIFICATE-----';
```

**Related Information**  


[DROP CERTIFICATE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-certificate-statement-for-data-lake-relational-engine-sap-hana-db-managed-5823712.md "Drops a certificate from the database.")

[CREATE PSE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-pse-statement-for-data-lake-relational-engine-sap-hana-db-managed-bc673db.md "Create a personal security environment (PSE).")

[SYSCERTIFICATE System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../070-system-views/syscertificate-system-view-for-data-lake-relational-engine-sap-hana-db-managed-cad9c1f.md "Each row of the SYSCERTIFICATE system view stores a certificate in text PEM-format. This view includes certificates with and without an associated PSE.")

[CREATE CERTIFICATE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/816b6bb36ce21014a7a7a27482e677e1.html "Adds or replaces a certificate in the database using the given file or string.") :arrow_upper_right:

