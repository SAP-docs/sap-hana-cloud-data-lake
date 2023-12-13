<!-- loioa61caee684f21015b95df0220f3f0a38 -->

# DROP EXTERNLOGIN Statement for Data Lake Relational Engine

Drops an external login from the data lake Relational Engine system tables.



<a name="loioa61caee684f21015b95df0220f3f0a38__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP EXTERNLOGIN <login-name> 
   TO <remote-server>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61caee684f21015b95df0220f3f0a38__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<login-name\>*

</b></dt>
<dd>

Specifies the local user login name.



</dd><dt><b>

TO *<remote-server\>*

</b></dt>
<dd>

Specifies the name of the remote server. The alternate login name of the local user and password for that server is the external login that is deleted.



</dd>
</dl>



<a name="loioa61caee684f21015b95df0220f3f0a38__IQ_Usage"/>

## Remarks

Changes made by `DROP EXTERNLOGIN` do not take effect until the next connection to the remote server.

> ### Note:  
> For **required** parameters that accept variable names, the database server returns an error if any of the following conditions is true:
> 
> -   The variable does not exist
> -   The contents of the variable are NULL
> -   The variable exceeds the length allowed by the parameter
> -   The data type of the variable does not match that required by the parameter



<a name="loioa61caee684f21015b95df0220f3f0a38__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY USER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa61caee684f21015b95df0220f3f0a38__IQ_Side_Effects"/>

## Side Effects

Automatic commit



<a name="loioa61caee684f21015b95df0220f3f0a38__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by Open Client/Open Server



<a name="loioa61caee684f21015b95df0220f3f0a38__IQ_Examples"/>

## Examples

The following example drops the login `dba` from the remote database `mydb1`:

```
DROP EXTERNLOGIN dba TO mydb1;
```

**Related Information**  


[CREATE EXTERNLOGIN Statement for Data Lake Relational Engine](create-externlogin-statement-for-data-lake-relational-engine-a61766a.md "Assigns an alternate login name and password to be used when communicating with a remote server.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

