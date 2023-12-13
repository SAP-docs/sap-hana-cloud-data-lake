<!-- loiob8f3ed4beb9645e98dee8a2c50011263 -->

# REPLACE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Replaces all occurrences of a substring with another substring.



```
REPLACE ( <original-string>, <search-string>, <replace-string> );
```



<a name="loiob8f3ed4beb9645e98dee8a2c50011263__section_tsh_gd5_vrb"/>

## Parameters

If any argument is NULL, the function returns NULL.


<dl>
<dt><b>

*<original-string\>*

</b></dt>
<dd>

The string to be searched. This string can be any length.



</dd><dt><b>

*<search-string\>*

</b></dt>
<dd>

The string to be searched for and replaced with *<replace-string\>*. This string is limited to 255 bytes. If *<search-string\>* is an empty string, the original string is returned unchanged.



</dd><dt><b>

*<replace-string\>*

</b></dt>
<dd>

The replacement string, which replaces *<search-string\>*. This can be any length. If *<replace-string\>* is an empty string, all occurrences of *<search-string\>* are deleted.



</dd>
</dl>



<a name="loiob8f3ed4beb9645e98dee8a2c50011263__section_uqr_jd5_vrb"/>

## Result Set

-   LONG BINARY

-   LONG VARCHAR

-   LONG NVARCHAR


> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `REPLACE` in a `SELECT INTO` statement, you must use `CAST` and set `REPLACE` to the correct data type and size.



<a name="loiob8f3ed4beb9645e98dee8a2c50011263__section_nc5_md5_vrb"/>

## Remarks

The result data type of a `REPLACE` function is a `LONG VARCHAR`. If you use `REPLACE` in a `SELECT INTO` statement, you must use `CAST` and set `REPLACE` to the correct data type and size.

If all arguments are of binary data type, the `REPLACE` function behaves the same as the `BYTE_REPLACE` function.

There are two ways to work around this issue:

-   Declare a local temporary table, then perform an `INSERT`:

    ```
    DECLARE local temporary table #mytable 
      (name_column char(10)) on commit preserve rows;
    INSERT INTO #mytable SELECT REPLACE(name,'0','1')   FROM dummy_table01;
    ```

-   Use `CAST`:

    ```
    SELECT CAST(replace(name, '0', '1') AS Char(10)) into #mytable from dummy_table01;
    ```


If you need to control the width of the resulting column when *<replace-string\>* is wider than *<search-string\>*, use the `CAST` function. For example:

```
CREATE TABLE aa(a CHAR(5));
INSERT INTO aa VALUES('CCCCC');
COMMIT;
SELECT a, CAST(REPLACE(a,'C','ZZ') AS CHAR(5)) FROM aa;
```



<a name="loiob8f3ed4beb9645e98dee8a2c50011263__section_wrl_nd5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loiob8f3ed4beb9645e98dee8a2c50011263__section_ldx_nd5_vrb"/>

## Examples

-   The following statement returns the value "xx.def.xx.ghi":

    ```
    SELECT REPLACE( 'abc.def.abc.ghi', 'abc', 'xx' ) FROM iq_dummy;
    ```

-   The following statement generates a result set containing `ALTER PROCEDURE` statements, which when executed, repair stored procedures that reference a table that has been renamed \(to be useful, the table name must be unique\):

    ```
    SELECT REPLACE(
      replace(proc_defn,'OldTableName','NewTableName'),
      'create procedure',
      'alter procedure')
    FROM SYS.SYSPROCEDURE
    WHERE proc_defn LIKE '%OldTableName%';
    ```

-   Use a separator other than the comma for the `LIST` function:

    ```
    SELECT REPLACE( list( table_id ), ',', '--')
    FROM  SYS.ISYSTAB
    WHERE table_id <= 5;
    ```


**Related Information**  


[REPLACE Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a579952184f210159e17940c17a6d8f7.html "Replaces all occurrences of a substring with another substring.") :arrow_upper_right:

