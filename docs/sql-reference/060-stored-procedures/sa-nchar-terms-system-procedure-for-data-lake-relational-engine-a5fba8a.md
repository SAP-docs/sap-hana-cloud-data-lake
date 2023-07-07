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


<dl>
<dt><b>

*<char-string\>*

</b></dt>
<dd>

The `NCHAR` string you are parsing.



</dd><dt><b>

*<text-config-name\>*

</b></dt>
<dd>

\(Optional\) The text configuration object to apply when processing the string. The default value is '`default_nchar`'.



</dd><dt><b>

*<owner\>*

</b></dt>
<dd>

\(Optional\) The owner of the specified text configuration object. The default value is DBA.



</dd>
</dl>



<a name="loioa5fba8a784f21015abe39fe3a6d391ea__iq_iquda_92"/>

## Remarks

You can use `sa_nchar_terms` to find out how a string is interpreted when the settings for a text configuration object are applied. This can be helpful when you want to know what terms would be dropped during indexing or from a query string.

The syntax for `sa_nchar_terms` is similar to the syntax for the `sa_char_terms` system procedure.

> ### Note:  
> The `NCHAR` data type is supported only for `IN SYSTEM` tables.



<a name="loioa5fba8a784f21015abe39fe3a6d391ea__iq_iquda_93"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



<a name="loioa5fba8a784f21015abe39fe3a6d391ea__section_sfr_3ss_mbb"/>

## Side Effects

None

