<!-- loioa4db1be484f21015bfe3fc26275f8447 -->

# sp\_iqmpxvalidate Procedure for Data Lake Relational Engine

Checks the multiplex cluster configuration for inconsistencies.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
call dbo.sp_iqmpxvalidate( 'Y' )
```



<a name="loioa4db1be484f21015bfe3fc26275f8447__section_fqg_g4g_nbb"/>

## Returns

Returns a severity result to the caller; values are:

-   0 – No errors detected
-   1 – Dynamic state isn't as expected.
-   2 – Nonfatal configuration error; for example, multiplex operation impaired.
-   3 – Fatal configuration problem; for example, one or more nodes doesn't start.



<a name="loioa4db1be484f21015bfe3fc26275f8447__iq_iqmpx_259"/>

## Remarks

Executes multiple checks on tables `SYS.SYSIQDBFILE` and other multiplex events and stored procedures. May run on any node.

Returns rows listing all errors and their severity. If called interactively, with the optional calling parameter 'N', returns only the severity status.

Each error indicates its severity. If there are no errors, the procedure returns `No errors detected`.



<a name="loioa4db1be484f21015bfe3fc26275f8447__iq_iqmpx_258"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md).



## Side Effects

None

