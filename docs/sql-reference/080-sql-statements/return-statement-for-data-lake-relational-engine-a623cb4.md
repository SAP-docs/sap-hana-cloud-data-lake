<!-- loioa623cb4484f21015bfd3efd8ac01df2f -->

# RETURN Statement for Data Lake Relational Engine

Exits a function or procedure unconditionally, optionally providing a return value. Statements following `RETURN` are not executed.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
RETURN [ ( <expression> ) ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa623cb4484f21015bfd3efd8ac01df2f__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

If supplied, the value of *<expression\>* is returned as the value of the function or procedure.

Within a function, the expression should be of the same data type as the RETURN data type of the function.



</dd>
</dl>



<a name="loioa623cb4484f21015bfd3efd8ac01df2f__IQ_Usage"/>

## Remarks

`RETURN` is used in procedures for Transact-SQL-compatibility, and is used to return an integer error code.



<a name="loioa623cb4484f21015bfd3efd8ac01df2f__IQ_Permissions"/>

## Privileges

None



<a name="loioa623cb4484f21015bfd3efd8ac01df2f__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – Transact-SQL procedures use the RETURN statement to return an integer error code.



<a name="loioa623cb4484f21015bfd3efd8ac01df2f__IQ_Examples"/>

## Examples

-   The following example returns the product of three numbers:

    ```
    CREATE FUNCTION product ( a numeric,
                    b numeric ,
                    c numeric)
    RETURNS numeric
    BEGIN
      RETURN ( a * b * c ) ;
    END
    ```

-   The following example calculates the product of three numbers:

    ```
    SELECT product (2, 3, 4)
    ```

    ```
    product (2,3,4)
    24
    ```

-   The following example avoids executing a complex query, if it is meaningless:

    ```

    ```


**Related Information**  


[BEGIN … END Statement for Data Lake Relational Engine](begin-end-statement-for-data-lake-relational-engine-a6142de.md "Groups SQL statements together.")

[CREATE PROCEDURE Statement for Data Lake Relational Engine](create-procedure-statement-for-data-lake-relational-engine-a6185b2.md "Creates a new user-defined SQL procedure in the database.")

