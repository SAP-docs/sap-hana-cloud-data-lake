<!-- loio52950a0cb81b4e09a835e1c464f11a64 -->

# SQLFLAGGER Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the conformity of a given SQL statement to a specified standard.



```
SQLFLAGGER ( <sql-standard-string>, <sql-statement-string> );
```



<a name="loio52950a0cb81b4e09a835e1c464f11a64__section_ifv_ww5_vrb"/>

## Parameters


<dl>
<dt><b>

*<sql-standard-string\>*

</b></dt>
<dd>

The standard level against which to test compliance. Possible values are the same as for the `SQL_FLAGGER_ERROR_LEVEL` database option:

-   `SQL:2003/Core` – test for conformance to core SQL/2003 syntax.
-   `SQL:2003/Package` – test for conformance to full SQL/2003 syntax.
-   `SQL:1999/Core` – test for conformance to core SQL/1999 syntax.
-   `SQL:1999/Package` – test for conformance to full SQL/1999 syntax.
-   `SQL:1992/Entry` – test for conformance to entry-level SQL/1992 syntax.
-   `SQL:1992/Intermediate` – test for conformance to intermediate-level SQL/1992 syntax.
-   `SQL:1992/Full` – test for conformance to full-SQL/1992 syntax.



</dd><dt><b>

*<sql-statement-string\>*

</b></dt>
<dd>

The SQL statement to check for conformance.



</dd>
</dl>



<a name="loio52950a0cb81b4e09a835e1c464f11a64__section_v5j_xw5_vrb"/>

## Result Set

LONG VARCHAR

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `SQLFLAGGER` in a `SELECT INTO` statement, you must use `CAST` and set `SQLFLAGGER` to the correct data type and size.



<a name="loio52950a0cb81b4e09a835e1c464f11a64__section_fxs_xw5_vrb"/>

## Remarks

You can also use the iqsqlpp SQL Preprocessor Utility to flag any Embedded SQL that is not part of a specified set of SQL92. See *iqsqlpp SQL Preprocessor Utility* in the *Utility Guide*.



<a name="loio52950a0cb81b4e09a835e1c464f11a64__section_lyh_yw5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loio52950a0cb81b4e09a835e1c464f11a64__section_q1r_yw5_vrb"/>

## Examples

-   The following statement shows an example of the message that is returned when a disallowed extension is found:

    ```
    SELECT SQLFLAGGER( 'SQL:2003/Package',
         'SELECT top 1 dummy_col FROM sys.dummy ORDER BY dummy_col' );
    ```

    This statement returns the message `'0AW03 Disallowed language extension detected in syntax near 'top' on line 1'`.

-   The following statement returns '00000' because it contains no disallowed extensions:

    ```
    SELECT SQLFLAGGER( 'SQL:2003/Package', 'SELECT dummy_col FROM sys.dummy' );
    ```


**Related Information**  


[SQLFLAGGER Function \[Miscellaneous\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a581e75f84f210158c3cd3ba6b97a9eb.html "Returns the conformity of a given SQL statement to a specified standard.") :arrow_upper_right:

