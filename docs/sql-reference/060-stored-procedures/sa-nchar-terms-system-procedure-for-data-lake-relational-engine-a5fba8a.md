<!-- loioa5fba8a784f21015abe39fe3a6d391ea -->

# sa\_nchar\_terms System Procedure for Data Lake Relational Engine

Breaks an `NCHAR` string into terms and returns each term as a row along with its position.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_nchar_terms
   ( '<char-string>' [ , '<text-config-name>' [, '<owner>' ] ] ] )
```



<a name="loioa5fba8a784f21015abe39fe3a6d391ea__iq_iquda_91"/>

## Parameters

 *<char-string\>*
 :   The `NCHAR` string you are parsing.

  *<text-config-name\>*
 :   \(Optional\) The text configuration object to apply when processing the string. The default value is '`default_nchar`'.

  *<owner\>*
 :   \(Optional\) The owner of the specified text configuration object. The default value is DBA.

 

<a name="loioa5fba8a784f21015abe39fe3a6d391ea__iq_iquda_92"/>

## Remarks

You can use `sa_nchar_terms` to find out how a string is interpreted when the settings for a text configuration object are applied. This can be helpful when you want to know what terms would be dropped during indexing or from a query string.

The syntax for `sa_nchar_terms` is similar to the syntax for the `sa_char_terms` system procedure.

> ### Note:  
> The `NCHAR` data type is supported only for `IN SYSTEM` tables.



<a name="loioa5fba8a784f21015abe39fe3a6d391ea__iq_iquda_93"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md).



<a name="loioa5fba8a784f21015abe39fe3a6d391ea__section_sfr_3ss_mbb"/>

## Side Effects

None

