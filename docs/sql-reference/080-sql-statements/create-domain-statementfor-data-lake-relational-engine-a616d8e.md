<!-- loioa616d8e584f2101588c5f0f67774d346 -->

# CREATE DOMAIN Statementfor Data Lake Relational Engine

Creates a user-defined data type in the database.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE { DOMAIN | DATATYPE } <domain-name> <data-type>
   … [ NOT ] NULL ]
   … [ DEFAULT <default-value> ]
```

```
<default-value> ::=
   {<special-value> 
   | <string> 
   | <global variable> 
   | [ - ] <number> 
   | ( <constant-expression> ) 
   | <built-in-function>( <constant-expression> ) 
   | AUTOINCREMENT 
   | CURRENT DATABASE 
   | CURRENT REMOTE USER 
   | NULL 
   | TIMESTAMP 
   | LAST USER }
```

```
<special-value> ::=
   { CURRENT 
      { DATE 
      | TIME 
      | TIMESTAMP 
      | USER 
      | PUBLISHER } 
   | USER }
```



<a name="loioa616d8e584f2101588c5f0f67774d346__IQ_Parameters"/>

## Parameters

 *<data-type\>*
 :   Built-in data type, with precision and scale.

    You can also specify a %TYPE or %ROWTYPE attribute to set the data type to the data type of a column or row in a table or view. However, specifying a table reference variable for the %ROWTYPE \(TABLE REF \(table-reference-variable\) %ROWTYPE\) is not allowed.

 

<a name="loioa616d8e584f2101588c5f0f67774d346__IQ_Usage"/>

## Remarks

User-defined data types are aliases for built-in data types, including precision and scale values, where applicable. They improve convenience and encourage consistency in the database.

> ### Note:  
> Use CREATE DOMAIN, rather than CREATE DATATYPE, as CREATE DOMAIN is the ANSI/ISO SQL3 term.

The user who creates a data type is automatically made the owner of that data type. No owner can be specified in the CREATE DATATYPE statement. The user-defined data type name must be unique, and all users can access the data type without using the owner as prefix.

User-defined data types are objects within the database. Their names must conform to the rules for identifiers. User-defined data type names are always case-insensitive, as are built-in data type names.

By default, user-defined data types allow NULLs unless the allow\_nulls\_by\_default database option is set to OFF. In this case, new user-defined data types by default do not allow NULLs. The nullability of a column created on a user-defined data type depends on the setting of the definition of the user-defined data type, not on the setting of the allow\_nulls\_by\_default option when the column is referenced. Any explicit setting of NULL or NOT NULL in the column definition overrides the user-defined data type setting.

The CREATE DOMAIN statement allows you to specify DEFAULT values on user-defined data types. The DEFAULT value specification is inherited by any column defined on the data type. Any DEFAULT value explicitly specified on the column overrides that specified for the data type.

The CREATE DOMAIN statement lets you incorporate a rule, called a CHECK condition, into the definition of a user-defined data type.

Data lake Relational Engine enforces CHECK constraints for base, global temporary, and local temporary tables, and user-defined data types.

To drop the data type from the database, use the DROP statement. You must be either the owner of the data type or have the CREATE DATATYPE or CREATE ANY OBJECT system privilege in order to drop a user-defined data type.



<a name="loioa616d8e584f2101588c5f0f67774d346__IQ_Permissions"/>

## Privileges

Requires one of:

-   CREATE DATATYPE system privilege
-   CREATE ANY OBJECT system privilege

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa616d8e584f2101588c5f0f67774d346__IQ_Side_Effects"/>

## Side Effects

Automatic commit



<a name="loioa616d8e584f2101588c5f0f67774d346__IQ_Standards"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loioa616d8e584f2101588c5f0f67774d346__IQ_Examples"/>

## Examples

The following example creates a data type named address, which holds a 35-character string, and which may be NULL:

```
CREATE DOMAIN address CHAR( 35 ) NULL
```

**Related Information**  


[DROP Statement for Data Lake Relational Engine](drop-statement-for-data-lake-relational-engine-a61c216.md "Removes objects from the database.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

