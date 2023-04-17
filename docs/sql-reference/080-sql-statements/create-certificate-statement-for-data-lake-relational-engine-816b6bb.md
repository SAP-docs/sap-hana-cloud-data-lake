<!-- loio816b6bb36ce21014a7a7a27482e677e1 -->

# CREATE CERTIFICATE Statement for Data Lake Relational Engine

Adds or replaces a certificate in the database from the given file or string.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE [ OR REPLACE ] CERTIFICATE <certificate-name>
   [ PURPOSE  FOR PROVIDER <provider_name> ]
   FROM { <certificate-string> | <variable-name> }

```



## Parameters

 PURPOSE clause
 :   Specifies the provider of the purpose for the certificate.

  FROM clause
 :   Specifies a string or variable containing a certificate.

 

## Remarks

The CREATE CERTIFICATE statement adds or replaces a certificate in the database from the given string or variable. The string or variable should contain either a binary DER-format certificate or a text PEM-format certificate. DER-format certificates are converted and stored as PEM certificates.

Certificates that are stored in the database can be used by web service procedures and functions that make secure HTTPS connections to a web server. Certificates with a specified PURPOSE can be used for user authentication.

The certificate is validated at log in time, not when the certificate is created.

When you add a certificate, it is added to the ISYSCERTIFICATE system table. Use the corresponding system view SYSCERTIFICATE to view the table.

The CREATE CERTIFICATE statement is not used to create an actual certificate. Use the Certificate Creation utility \(createcert\) to do this.



## Privileges

You must have the MANAGE CERTIFICATES and READ FILE system privileges.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



## Side Effects

Automatic commit.



## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 

<a name="loio816b6bb36ce21014a7a7a27482e677e1__section_gwx_f3p_p4b"/>

## Example

This example creates a certificate with a JWT purpose.

```
CREATE CERTIFICATE my_cert1
PURPOSE JWT FOR PROVIDER my_jwt_provider
FROM '-----BEGIN CERTIFICATE-----
...-----END CERTIFICATE-----':
```

**Related Information**  


[CREATE JWT PROVIDER Statement for Data Lake Relational Engine](create-jwt-provider-statement-for-data-lake-relational-engine-49b7ee1.md "Defines a JWT provider in the data lake Relational Engine database.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[DROP JWT PROVIDER Statement for Data Lake Relational Engine](drop-jwt-provider-statement-for-data-lake-relational-engine-c20d71c.md "Drops a JWT provider from the data lake Relational Engine database.")

