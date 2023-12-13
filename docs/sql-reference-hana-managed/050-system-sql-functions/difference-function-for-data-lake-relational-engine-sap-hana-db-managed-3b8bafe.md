<!-- loio3b8bafe468ce4160b52b7b25a5de50a0 -->

# DIFFERENCE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Compares two strings, evaluates the similarity between them, and returns a value from 0 to 4.



```
DIFFERENCE ( <string-expression1>, <string-expression2> );
```



<a name="loio3b8bafe468ce4160b52b7b25a5de50a0__section_pgd_qzl_srb"/>

## Parameters


<dl>
<dt><b>

*<string-expression1\>*

</b></dt>
<dd>

The first string to compare.



</dd><dt><b>

*<string-expression2\>*

</b></dt>
<dd>

The second string to compare.



</dd>
</dl>



<a name="loio3b8bafe468ce4160b52b7b25a5de50a0__section_rzk_bm3_wrb"/>

## Result Set

SMALLINT



<a name="loio3b8bafe468ce4160b52b7b25a5de50a0__section_gkf_cm3_wrb"/>

## Remarks

The best match is 4.



<a name="loio3b8bafe468ce4160b52b7b25a5de50a0__section_lhz_rzl_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio3b8bafe468ce4160b52b7b25a5de50a0__section_snj_szl_srb"/>

## Examples

-   The following statement returns the value 4:

    ```
    SELECT DIFFERENCE( 'Smith', 'Smith' ) FROM iq_dummy;
    ```

-   The following statement returns the value 4:

    ```
    SELECT DIFFERENCE( 'Smith', 'Smyth' ) FROM iq_dummy;
    ```

-   The following statement returns the value 3:

    ```
    SELECT DIFFERENCE( 'Smith', 'Sweeney' ) FROM iq_dummy;
    ```

-   The following statement returns the value 2:

    ```
    SELECT DIFFERENCE( 'Smith', 'Jones' ) FROM iq_dummy;
    ```

-   The following statement returns the value 1:

    ```
    SELECT DIFFERENCE( 'Smith', 'Rubin' ) FROM iq_dummy;
    ```

-   The following statement returns the value 0:

    ```
    SELECT DIFFERENCE( 'Smith', 'Wilkins' ) FROM iq_dummy;
    ```


**Related Information**  


[DIFFERENCE Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a54d8aac84f210158ef283ad984de764.html "Compares two strings, evaluates the similarity between them, and returns a value from 0 to 4.") :arrow_upper_right:

