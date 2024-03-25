<!-- loioc22eaf42bb524cc58ef660f84743c934 -->

# DROP CERTIFICATE STATEMENT for Data Lake Relational Engine

Drops a certificate from the database.



<a name="loioc22eaf42bb524cc58ef660f84743c934__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP CERTIFICATE [IF EXISTS ] <certificate-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioc22eaf42bb524cc58ef660f84743c934__drop_certificate_param1"/>

## Parameters


<dl>
<dt><b>

IF EXISTS

</b></dt>
<dd>

Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.



</dd>
</dl>



<a name="loioc22eaf42bb524cc58ef660f84743c934__drop_certificate_remarks1"/>

## Remarks

None



<a name="loioc22eaf42bb524cc58ef660f84743c934__drop_certificate_priv1"/>

## Privileges



### 

Requires one of the following:

-   To manage self-owned certificates requires the MANAGE ONWER CERTIFICATES system privilege.
-   To manage certificates owned by other requires the MANAGE CERTIFICATES system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioc22eaf42bb524cc58ef660f84743c934__drop_certificate_side_effects1"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loioc22eaf42bb524cc58ef660f84743c934__drop_certificate_standards1"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loioc22eaf42bb524cc58ef660f84743c934__drop_certificate_examples1"/>

## Examples

This example drops the certificate mycert1:

```
DROP CERTIFICATE mycert1;
```

**Related Information**  


[CREATE CERTIFICATE Statement for Data Lake Relational Engine](create-certificate-statement-for-data-lake-relational-engine-816b6bb.md "Adds or replaces a certificate in the database using the given file or string.")

[DROP CERTIFICATE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/5823712c23734d86b5498688b5a0b0df.html "Drops a certificate from the database.") :arrow_upper_right:

