<!-- loio53742a28df0f40deb5cd7a9784fc1a55 -->

# ALTER PSE Statement for Data Lake Relational Engine

Modifies an existing personal security environment \(PSE\).



<a name="loio53742a28df0f40deb5cd7a9784fc1a55__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER PSE <pse-name> 
   { <certificate-clause>
   | <set-own-certificate-clause>
   | <unset-own-certificate-clause> }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio53742a28df0f40deb5cd7a9784fc1a55__alter_pse_param1"/>

## Parameters


<dl>
<dt><b>

*<certificate-clause\>*

</b></dt>
<dd>

Adds or drops certificate\(s\) to and from the PSE.

```
<certificate-clause> ::= { ADD | DROP } CERTIFICATE ( 
   { <certificate-name>[, <certificate-name>[,...] ]
   | <certificate-id>[, <certificate-id>[,...] ] } );
```


<dl>
<dt><b>

*<certificate-name\>*

</b></dt>
<dd>

```
<certificate-name> ::= <simple-identifier>;
```



</dd><dt><b>

*<certificate-id\>*

</b></dt>
<dd>

```
<certificate-id> ::= <object-id>;
```



</dd>
</dl>



</dd><dt><b>

*<set-own-certificate-clause\>*

</b></dt>
<dd>

Set the own certificate and private key.

```
<set-own-certificate-clause> ::= SET OWN CERTIFICATE <certificate-content>;
```


<dl>
<dt><b>

*<certificate-content\>*

</b></dt>
<dd>

The *<certificate-content\>* string may contain one or more certificates in the PEM format and the private key of the own certificate. One of the certificates is the own certificate and the other certificate\(s\) are intermediate chain certificates completing the trust chain from the own certificate to the root certificate, which the peer trusts. The own certificate and the order of the certificates forming a chain can be identified by the issuer or subject relationship. If the PSE already has an own certificate assigned, it is replaced.



</dd>
</dl>



</dd><dt><b>

*<unset-own-certificate-clause\>*

</b></dt>
<dd>

Removes the own certificate, any intermediate chain certificates, and the private key.

```
<unset-own-certificate-clause> ::= UNSETSET OWN CERTIFICATE;
```



</dd>
</dl>



<a name="loio53742a28df0f40deb5cd7a9784fc1a55__alter_pse_remarks1"/>

## Remarks

None



<a name="loio53742a28df0f40deb5cd7a9784fc1a55__alter_pse_priv1"/>

## Privileges



### 

You own the PSE.



<a name="loio53742a28df0f40deb5cd7a9784fc1a55__alter_pse_side_effects1"/>

## Side Effects

Automatic commit.



<a name="loio53742a28df0f40deb5cd7a9784fc1a55__alter_pse_examples1"/>

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


[CREATE PSE Statement for Data Lake Relational Engine](create-pse-statement-for-data-lake-relational-engine-cda6e32.md "Create a personal security environment (PSE).")

[DROP PSE Statement for Data Lake Relational Engine](drop-pse-statement-for-data-lake-relational-engine-2918c50.md "Removes a personal security environment (PSE) from the database.")

[ALTER PSE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/056ee2c16cd548e3a811170533f684e7.html "Modifies an existing personal security environment (PSE).") :arrow_upper_right:

