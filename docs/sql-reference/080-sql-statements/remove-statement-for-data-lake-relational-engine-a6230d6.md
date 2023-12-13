<!-- loioa6230d6784f21015819abbfa7efd1fde -->

# REMOVE Statement for Data Lake Relational Engine

Removes a class, a package, or a JAR file from a database. Removed classes are no longer available for use as a variable type. Any class, package, or JAR to be removed must already be installed.



<a name="loioa6230d6784f21015819abbfa7efd1fde__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
REMOVE JAVA <classes_to_remove>

<classes_to_remove>
   { CLASS <java_class_name> [, <java_class_name> ]… 
   | PACKAGE <java_package_name> [, <java_package_name> ]… 
   | JAR <jar_name> [, <jar_name> ]… [ RETAIN CLASSES ] };
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa6230d6784f21015819abbfa7efd1fde__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

CLASS *<java\_class\_name\>*

</b></dt>
<dd>

Specifies the name of one or more Java classes to be removed. Those classes must be installed classes in the current database.



</dd><dt><b>

PACKAGE *<java\_package\_name\>*

</b></dt>
<dd>

Specifies the name of one or more Java packages to be removed. Those packages must be the name of packages in the current database.



</dd><dt><b>

JAR *<jar\_name\>*

</b></dt>
<dd>

Specifies a character string value of maximum length 255. Each *<jar\_name\>* must be equal to the *<jar\_name\>* of a retained JAR in the current database. Equality of *<jar\_name\>* is determined by the character string comparison rules of the SQL system.



</dd><dt><b>

RETAIN CLASSES

</b></dt>
<dd>

The specified JARs are no longer retained in the database, and the retained classes have no associated JAR. If RETAIN CLASSES is specified, this is the only action of the `REMOVE` statement.



</dd>
</dl>



<a name="loioa6230d6784f21015819abbfa7efd1fde__IQ_Permissions"/>

## Privileges

Requires one of:

-   You own the object
-   MANAGE ANY EXTERNAL OBJECT system privilege

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa6230d6784f21015819abbfa7efd1fde__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar.
-   SAP database products – not supported by SAP Adaptive Server Enterprise. A similar feature is available in an SAP ASE-compatible manner using nested transactions.



<a name="loioa6230d6784f21015819abbfa7efd1fde__IQ_Examples"/>

## Examples

The following example removes a Java class named "Demo" from the current database:

```
REMOVE JAVA CLASS Demo;
```

**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

