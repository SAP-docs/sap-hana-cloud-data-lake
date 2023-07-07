<!-- loio3be48e516c5f1014911fbb7c9231737e -->

# DROP SEQUENCE Statement for Data Lake Relational Engine

Drops a sequence.This statement applies to data lake Relational Engine catalog store tables only. 



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP SEQUENCE [ <owner>.]<sequence-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



## Remarks

If the named sequence cannot be located, an error message is returned. When you drop a sequence, all synonyms for the name of the sequence are dropped automatically by the database server.



<a name="loio3be48e516c5f1014911fbb7c9231737e__section_w5t_cdy_m2b"/>

## Privileges

Requires one of:

-   You own of the sequence
-   DROP ANY SEQUENCE system privilege

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



## Side Effects

Automatic commit.



## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Sequences comprise optional ANSI/ISO SQL Language Feature T176.



</dd>
</dl>



The following example creates and then drops a sequence named Test:

```
CREATE SEQUENCE Test
START WITH 4
INCREMENT BY 2
NO MAXVALUE
NO CYCLE
CACHE 15;
DROP SEQUENCE Test;
```

**Related Information**  


[ALTER SEQUENCE Statement for Data Lake Relational Engine](alter-sequence-statement-for-data-lake-relational-engine-3be43c9.md "Alters a sequence. This statement applies to data lake Relational Engine catalog store tables only.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[CREATE SEQUENCE Statement for Data Lake Relational Engine](create-sequence-statement-for-data-lake-relational-engine-3be47d4.md "Creates a sequence that can be used to generate primary key values that are unique across multiple tables, and for generating default values for a table. This statement applies to data lake Relational Engine catalog store tables only.")

