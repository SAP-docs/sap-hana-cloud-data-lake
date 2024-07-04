<!-- loio816b6bb36ce21014a7a7a27482e677e1 -->

# CREATE CERTIFICATE Statement for Data Lake Relational Engine

Adds or replaces a certificate in the database using the given file or string.



<a name="loio816b6bb36ce21014a7a7a27482e677e1__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE [ OR REPLACE ] CERTIFICATE <certificate-name>
   [ PURPOSE { JWT | X509 } FOR PROVIDER <provider_name> ]
   FROM { <certificate-string> | <variable-name> }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio816b6bb36ce21014a7a7a27482e677e1__create_certificate_param1"/>

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



<a name="loio816b6bb36ce21014a7a7a27482e677e1__create_certificate_remarks1"/>

## Remarks

The string or file should contain either a binary DER-format certificate or a text PEM-format certificate. DER-format certificates are converted and stored as PEM certificates.

Certificates that are stored in the database can be used by web service procedures and functions that make secure HTTPS connections to a web server. Certificates with a specified PURPOSE can be used for user authentication.

The certificate is validated at login time, not when the certificate is created.

Use the SYSCERTIFICATE system view to display a list of certificates

The CREATE CERTIFICATE statement is not used to create an actual certificate. Use the Certificate Creation utility \(createcert\) to do this.



<a name="loio816b6bb36ce21014a7a7a27482e677e1__create_certificate_priv1"/>

## Privileges



### 

Requires one of the following:

-   To manage self-owned certificates requires the MANAGE OWNER CERTIFICATES system privilege.
-   To manage certificates owned by other requires the MANAGE CERTIFICATES system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loio816b6bb36ce21014a7a7a27482e677e1__create_certificate_side_effects1"/>

## Side Effects

Automatic commit.



<a name="loio816b6bb36ce21014a7a7a27482e677e1__create_certificate_standards1"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



<a name="loio816b6bb36ce21014a7a7a27482e677e1__create_certificate_examples1"/>

## Examples

This example creates a certificate with a JWT purpose.

```
CREATE CERTIFICATE my_cert1
PURPOSE JWT FOR PROVIDER my_jwt_provider
FROM '-----BEGIN CERTIFICATE-----
...-----END CERTIFICATE-----';
```

This example creates a certificate with an X.509 purpose.

```
CREATE CERTIFICATE my_cert2
PURPOSE X509 FOR PROVIDER my_X509_provider
FROM '-----BEGIN CERTIFICATE-----
...-----END CERTIFICATE-----';
```

**Related Information**  


[DROP CERTIFICATE Statement for Data Lake Relational Engine](drop-certificate-statement-for-data-lake-relational-engine-c22eaf4.md "Drops a certificate from the database.")

[CREATE JWT PROVIDER Statement for Data Lake Relational Engine](create-jwt-provider-statement-for-data-lake-relational-engine-49b7ee1.md "Defines a JWT provider in the data lake Relational Engine database.")

[CREATE X509 PROVIDER Statement for Data Lake Relational Engine](create-x509-provider-statement-for-data-lake-relational-engine-fe6ef48.md "Create an X.509 provider in the database.")

[CREATE PSE Statement for Data Lake Relational Engine](create-pse-statement-for-data-lake-relational-engine-cda6e32.md "Create a personal security environment (PSE).")

[SYSCERTIFICATE System View for Data Lake Relational Engine](../070-system-and-monitoring-views/syscertificate-system-view-for-data-lake-relational-engine-a34ee8b.md "Each row of the SYSCERTIFICATE system view stores a certificate in text PEM-format. This view includes certificates with and without an associated PSE.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[CREATE CERTIFICATE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/d827f8589599403c94bd8700114c9e46.html "Adds or replaces a certificate in the database using the given file or string.") :arrow_upper_right:

