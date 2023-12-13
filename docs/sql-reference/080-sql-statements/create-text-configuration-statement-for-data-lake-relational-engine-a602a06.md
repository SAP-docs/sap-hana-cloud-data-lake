<!-- loioa602a06684f21015b7f78f0f1a3ea0d9 -->

# CREATE TEXT CONFIGURATION Statement for Data Lake Relational Engine

Creates a text configuration object using another text configuration object as a template.



<a name="loioa602a06684f21015b7f78f0f1a3ea0d9__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE TEXT CONFIGURATION [ { <owner> | <schema-name> }.]<new-config-name> 
   FROM [ { <owner> | <schema-name> }.]<existing-config-name>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa602a06684f21015b7f78f0f1a3ea0d9__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

FROM

</b></dt>
<dd>

Specifies the name of a text configuration object to use as the template for creating the new text configuration object. The names of the default text configuration objects are DEFAULT\_CHAR and DEFAULT\_NCHAR. DEFAULT\_CHAR is supported for data lake Relational Engine tables only; DEFAULT\_NCHAR is supported on SAP SQL Anywhere tables only.



</dd>
</dl>



<a name="loioa602a06684f21015b7f78f0f1a3ea0d9__IQ_Usage"/>

## Remarks

Create a text configuration object using another text configuration object as a template, then alter the options as needed using the `ALTER TEXT CONFIGURATION` statement.

To view the list of all text configuration objects and their settings in the database, query the `SYSTEXTCONFIG` system view.



<a name="loioa602a06684f21015b7f78f0f1a3ea0d9__IQ_Permissions"/>

## Privileges

-   To create a self-owned text configuration requires the CREATE TEXT CONFIGURATION system privilege.
-   To create a text configuration owned by another user requires one of:
    -   CREATE ANY TEXT CONFIGURATION system privilege.
    -   CREATE ANY OBJECT system privilege.
    -   CREATE ANY object-level privilege on the schema if the text configuration is in a schema owned by another user.


All text configuration objects have PUBLIC access. Any user with privilege to create a `TEXT` index can use any text configuration object.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa602a06684f21015b7f78f0f1a3ea0d9__IQ_Side_Effects"/>

## Side Effects

Automatic commit



<a name="loioa602a06684f21015b7f78f0f1a3ea0d9__IQ_Examples"/>

## Examples

The following example creates a text configuration object, `max_term_sixteen`, using the `default_char` text configuration object:

```
CREATE TEXT CONFIGURATION max_term_sixteen FROM default_char;
```

**Related Information**  


[ALTER TEXT CONFIGURATION Statement for Data Lake Relational Engine](alter-text-configuration-statement-for-data-lake-relational-engine-a602402.md "Alters a text configuration object.")

[DROP TEXT CONFIGURATION Statement for Data Lake Relational Engine](drop-text-configuration-statement-for-data-lake-relational-engine-a602fed.md "Drops a text configuration object.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

