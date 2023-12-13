<!-- loioa62b99df84f21015bd98a592902abc4b -->

# Interactive SQL Options

Interactive SQL options change how Interactive SQL interacts with the database.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
SET [ TEMPORARY ] OPTION
... [ <userid>. | PUBLIC. ] <option-name> = [ <option-value> ];
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
SET PERMANENT;
```



</dd><dt><b>

Syntax 3

</b></dt>
<dd>

```
SET;
```



</dd>
</dl>



<a name="loioa62b99df84f21015bd98a592902abc4b__iq_refso_321"/>

## Parameters

```
<userid> ::=
   <identifier>, <string> or <host-variable>;
```

```
<option-name> ::=
   <identifier>, <string> or <host-variable>;
```

```
<option-value> ::=
   <host-variable> (indicator allowed), <string>, <identifier>,
   or <number>;
```



<a name="loioa62b99df84f21015bd98a592902abc4b__iq_refso_322"/>

## Remarks

In Syntax 1, you cannot use the `TEMPORARY` keyword between the `BEGIN` and `END` keywords of a compound statement.

In Syntax 2, `SET PERMANENT` stores all current Interactive SQL options in the `SYSOPTIONS` system table. These settings are automatically established every time Interactive SQL is started for the current user ID.

Syntax 3 is used to display all of the current option settings. If there are temporary options set for Interactive SQL or the database server, these are displayed; otherwise, the permanent option settings are displayed.



The available options are:

-   [DEFAULT\_ISQL\_ENCODING Option \[Interactive SQL\] for Data Lake Relational Engine](default-isql-encoding-option-interactive-sql-for-data-lake-relational-engine-a63407d.md)
-   [ON\_ERROR Option \[Interactive SQL\] for Data Lake Relational Engine](on-error-option-interactive-sql-for-data-lake-relational-engine-a6462f5.md)

**Related Information**  


[Transact-SQL Compatibility Options](transact-sql-compatibility-options-a62b3bb.md "Transact-SQL compatibility options allow data lake Relational Engine behavior to be compatible with SAP Adaptive Server Enterprise, or to both support old behavior and allow ISO SQL92 behavior.")

[Alphabetical List of Settable Options in Data Lake Relational Engine](alphabetical-list-of-settable-options-in-data-lake-relational-engine-a62bc88.md "Settable database options let you configure database behavior.")

