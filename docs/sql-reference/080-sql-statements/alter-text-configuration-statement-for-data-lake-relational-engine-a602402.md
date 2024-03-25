<!-- loioa602402c84f21015a00eb58f531612a0 -->

# ALTER TEXT CONFIGURATION Statement for Data Lake Relational Engine

Alters a text configuration object.



<a name="loioa602402c84f21015a00eb58f531612a0__section_tqv_vvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER TEXT CONFIGURATION [ { <owner> | <schema-name> }.]<config-name>
...{ STOPLIST <stoplist> 
...| DROP STOPLIST
...| { MINIMUM | MAXIMUM } TERM LENGTH <integer>
...| TERM BREAKER GENERIC }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa602402c84f21015a00eb58f531612a0__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

DROP *<stoplist\>*

</b></dt>
<dd>

A string expression used to create or replace the list of terms to ignore when building a TEXT index. Terms specified in this list are also ignored in a query. Separate stoplist terms with spaces.

Stoplist terms cannot contain whitespace and should not contain non-alphanumeric characters. Non-alphanumeric characters are interpreted as spaces and break the term into multiple terms. For example, “and/or” is interpreted as the two terms “and” and “or”. The maximum number of stoplist terms is 7999.



</dd><dt><b>

DROP STOPLIST

</b></dt>
<dd>

Use to drop the stoplist for a text configuration object.



</dd><dt><b>

MINIMUM TERM LENGTH

</b></dt>
<dd>

Specifies the minimum length, in characters, of a term to include in the TEXT index. The value specified in the MINIMUM TERM LENGTH clause is ignored when using NGRAM TEXT indexes. Terms that are shorter than this setting are ignored when building or refreshing the TEXT index. The value of this option must be greater than 0. If you set this option to be higher than MAXIMUM TERM LENGTH, the value of MAXIMUM TERM LENGTH is automatically adjusted to be the same as the new MINIMUM TERM LENGTH value.



</dd><dt><b>

MAXIMUM TERM LENGTH

</b></dt>
<dd>

With GENERIC TEXT indexes, specifies the maximum length, in characters, of a term to include in the TEXT index. Terms that are longer than this setting are ignored when building or refreshing the TEXT index. The value of MAXIMUM TERM LENGTH must be less than or equal to 60. If you set this option to be lower than MINIMUM TERM LENGTH, the value of MINIMUM TERM LENGTH is automatically adjusted to be the same as the new MAXIMUM TERM LENGTH value.



</dd><dt><b>

TERM BREAKER

</b></dt>
<dd>

Specifies the name of the algorithm to use for separating column values into terms.



</dd>
</dl>



<a name="loioa602402c84f21015a00eb58f531612a0__IQ_Usage"/>

## Remarks

TEXT indexes are dependent on a text configuration object. TEXT indexes use immediate refresh, and cannot be truncated; you must drop the indexes before you can alter the text configuration object. To view the settings for text configuration objects, query the SYSTEXTCONFIG system view.



<a name="loioa602402c84f21015a00eb58f531612a0__IQ_Permissions"/>

## Privileges

-   Requires one of the following:
-   -   You own the text configuration
-   ALTER ANY TEXT CONFIGURATION system privilege
-   ALTER ANY OBJECT system privilege
-   You own the schema containing the text configuration
-   ALTER object-level privilege on the schema containing the text configuration


See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa602402c84f21015a00eb58f531612a0__IQ_Side_Effects"/>

## Side Effects

Automatic commit



<a name="loioa602402c84f21015a00eb58f531612a0__IQ_Examples"/>

## Examples

-   The following example creates a text configuration object, `maxTerm16`, and then change the maximum term length to 16:

    ```
    CREATE TEXT CONFIGURATION maxTerm16 FROM default_char;
    ALTER TEXT CONFIGURATION maxTerm16 MAXIMUM TERM LENGTH 16;
    ```

-   The following example adds stoplist terms to the `maxTerm16` configuration object:

    ```
    ALTER TEXT CONFIGURATION maxTerm16
    STOPLIST 'because about therefore only';
    ```


**Related Information**  


[CREATE TEXT CONFIGURATION Statement for Data Lake Relational Engine](create-text-configuration-statement-for-data-lake-relational-engine-a602a06.md "Creates a text configuration object using another text configuration object as a template.")

[DROP TEXT CONFIGURATION Statement for Data Lake Relational Engine](drop-text-configuration-statement-for-data-lake-relational-engine-a602fed.md "Drops a text configuration object.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

