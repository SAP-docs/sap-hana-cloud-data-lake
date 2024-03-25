<!-- loio66b441998f6b490ca54f8314748c9331 -->

# SORTKEY Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Generates values that can be used to sort character strings based on alternate collation rules.



```
SORTKEY ( <string-expression> [, { <collation-id>
| <collation-name> [ ( <collation-tailoring-string> ) ] } ] );
```



<a name="loio66b441998f6b490ca54f8314748c9331__section_adf_cy5_vrb"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>* 

</b></dt>
<dd>

The string expression must contain characters that are encoded in the character set of the database and must be `STRING` data type.

If string-expression is NULL, the `SORTKEY` function returns a null value. An empty string has a different sort-order value than a null string from a database column.

There is no limit on the length of the input string that the `SORTKEY` function can handle. The result of `SORTKEY` is always limited to 1024 bytes and is `VARBINARY` data type. If the actual results exceed 1024 bytes, the result contains only the first 1024 bytes.



</dd><dt><b>

*<collation-id\>*

</b></dt>
<dd>

A variable, integer constant, or string that specifies the ID number of the sort order to use. This parameter applies only to SAP ASE collations, which can be referred to by their corresponding collation ID.



</dd><dt><b>

*<collation-name\>*

</b></dt>
<dd>

A string or character variable that specifies the name of the sort order to use. You can also specify the alias char\_collation, or, equivalently, db\_collation, to generate sort-keys as used by the CHAR collation in use by the database.

Similarly, you can specify the alias NCHAR\_COLLATION to generate sort-keys as used by the NCHAR collation in use by the database. However, data lake Relational Engine does not support NCHAR\_COLLATION for data lake Relational Engine-specific objects. NCHAR\_COLLATION is supported for SAP SQL Anywhere objects on a data lake Relational Engine server.



</dd><dt><b>

*<collation-tailoring-string\>*

</b></dt>
<dd>

\(Optional\) Specify collation tailoring options \(*<collation-tailoring-string\>*\) for additional control over sorting and comparison of characters. These options take the form of keyword=value pairs assembled in parentheses, following the collation name. For example:

```
'UCA(locale=es;case=LowerFirst;accent=respect);'
```

> ### Note:  
> All of the collation tailoring options are supported for SAP SQL Anywhere databases, when specifying the Unicode Collation Algorithm \(UCA\) collation. For all other collations, only case-sensitivity tailoring is supported.



</dd>
</dl>



<a name="loio66b441998f6b490ca54f8314748c9331__section_jgz_cy5_vrb"/>

## Result Set

BINARY



<a name="loio66b441998f6b490ca54f8314748c9331__section_qf3_dy5_vrb"/>

## Remarks

The `SORTKEY` function generates values that can be used to order results based on predefined sort order behavior. This allows you to work with character sort order behaviors that may not be available from the database collation. The returned value is a binary value that contains coded sort order information for the input string that is retained from the `SORTKEY` function.

For example, you can store the values returned by the `SORTKEY` function in a column with the source character string. The following `SELECT` statement retrieves data from table T1 in the sorted order of c1 according to the Thai dictionary:

```
SELECT rid, c1 from T1 ORDER BY SORTKEY(c1);
```

You instead store the value returned by `SORTKEY`in a column with the source character string. To retrieve the character data in the required order, the `SELECT` statement needs to include only an `ORDER BY` clause on the column that contains the results of running the `SORTKEY` function:

```
UPDATE T1 SET shadowc1=SORTKEY(c1) FROM T1
SELECT rid, c1 FROM T1 ORDER BY shadowc1;
```

The `SORTKEY` function guarantees that the values it returns for a given set of sort order criteria work for the binary comparisons that are performed on `VARBINARY` data types.

Generating sort-keys for queries can be expensive. As an alternative for frequently requested sort-keys, consider creating a computed column to hold the sort-key values, and then referencing that column in the `ORDER BY` clause of the query.

If you do not specify a collation name or collation ID, the default is Default Unicode multilingual.

Valid collations are as follows:

-   To see collations that are supported by data lake Relational Engine, listed by label, execute `iqinit -l`.

-   The SAP ASE collations are listed in the table below.


    <table>
    <tr>
    <th valign="top" rowspan="1">

    Description
    
    </th>
    <th valign="top" rowspan="1">

    Collation Name
    
    </th>
    <th valign="top" rowspan="1">

    Collation ID
    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    Default Unicode multilingual
    
    </td>
    <td valign="top" rowspan="1">
    
    default
    
    </td>
    <td valign="top" rowspan="1">
    
    0
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    CP 850 Alternative: no accent
    
    </td>
    <td valign="top" rowspan="1">
    
    altnoacc
    
    </td>
    <td valign="top" rowspan="1">
    
    39
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    CP 850 Alternative: lowercase first
    
    </td>
    <td valign="top" rowspan="1">
    
    altdict
    
    </td>
    <td valign="top" rowspan="1">
    
    45
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    CP 850 Western European: no case, preference
    
    </td>
    <td valign="top" rowspan="1">
    
    altnocsp
    
    </td>
    <td valign="top" rowspan="1">
    
    46
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    CP 850 Scandinavian dictionary
    
    </td>
    <td valign="top" rowspan="1">
    
    scandict
    
    </td>
    <td valign="top" rowspan="1">
    
    47
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    CP 850 Scandinavian: no case, preference
    
    </td>
    <td valign="top" rowspan="1">
    
    scannocp
    
    </td>
    <td valign="top" rowspan="1">
    
    48
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    GB Pinyin
    
    </td>
    <td valign="top" rowspan="1">
    
    gbpinyin
    
    </td>
    <td valign="top" rowspan="1">
    
    n/a
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    Binary sort
    
    </td>
    <td valign="top" rowspan="1">
    
    binary
    
    </td>
    <td valign="top" rowspan="1">
    
    50
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    Latin-1 English, French, German dictionary
    
    </td>
    <td valign="top" rowspan="1">
    
    dict
    
    </td>
    <td valign="top" rowspan="1">
    
    51
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    Latin-1 English, French, German no case
    
    </td>
    <td valign="top" rowspan="1">
    
    nocase
    
    </td>
    <td valign="top" rowspan="1">
    
    52
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    Latin-1 English, French, German no case, preference
    
    </td>
    <td valign="top" rowspan="1">
    
    nocasep
    
    </td>
    <td valign="top" rowspan="1">
    
    53
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    Latin-1 English, French, German no accent
    
    </td>
    <td valign="top" rowspan="1">
    
    noaccent
    
    </td>
    <td valign="top" rowspan="1">
    
    54
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    Latin-1 Spanish dictionary
    
    </td>
    <td valign="top" rowspan="1">
    
    espdict
    
    </td>
    <td valign="top" rowspan="1">
    
    55
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    Latin-1 Spanish no case
    
    </td>
    <td valign="top" rowspan="1">
    
    espnocs
    
    </td>
    <td valign="top" rowspan="1">
    
    56
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    Latin-1 Spanish no accent
    
    </td>
    <td valign="top" rowspan="1">
    
    espnoac
    
    </td>
    <td valign="top" rowspan="1">
    
    57
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    ISO 8859-5 Russian dictionary
    
    </td>
    <td valign="top" rowspan="1">
    
    rusdict
    
    </td>
    <td valign="top" rowspan="1">
    
    58
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    ISO 8859-5 Russian no case
    
    </td>
    <td valign="top" rowspan="1">
    
    rusnocs
    
    </td>
    <td valign="top" rowspan="1">
    
    59
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    ISO 8859-5 Cyrillic dictionary
    
    </td>
    <td valign="top" rowspan="1">
    
    cyrdict
    
    </td>
    <td valign="top" rowspan="1">
    
    63
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    ISO 8859-5 Cyrillic no case
    
    </td>
    <td valign="top" rowspan="1">
    
    cyrnocs
    
    </td>
    <td valign="top" rowspan="1">
    
    64
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    ISO 8859-7 Greek dictionary
    
    </td>
    <td valign="top" rowspan="1">
    
    elldict
    
    </td>
    <td valign="top" rowspan="1">
    
    65
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    ISO 8859-2 Hungarian dictionary
    
    </td>
    <td valign="top" rowspan="1">
    
    hundict
    
    </td>
    <td valign="top" rowspan="1">
    
    69
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    ISO 8859-2 Hungarian no accents
    
    </td>
    <td valign="top" rowspan="1">
    
    hunnoac
    
    </td>
    <td valign="top" rowspan="1">
    
    70
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    ISO 8859-2 Hungarian no case
    
    </td>
    <td valign="top" rowspan="1">
    
    hunnocs
    
    </td>
    <td valign="top" rowspan="1">
    
    71
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    ISO 8859-5 Turkish dictionary
    
    </td>
    <td valign="top" rowspan="1">
    
    turdict
    
    </td>
    <td valign="top" rowspan="1">
    
    72
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    ISO 8859-5 Turkish no accents
    
    </td>
    <td valign="top" rowspan="1">
    
    turnoac
    
    </td>
    <td valign="top" rowspan="1">
    
    73
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    ISO 8859-5 Turkish no case
    
    </td>
    <td valign="top" rowspan="1">
    
    turnocs
    
    </td>
    <td valign="top" rowspan="1">
    
    74
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    CP 874 \(TIS 620\) Royal Thai dictionary
    
    </td>
    <td valign="top" rowspan="1">
    
    thaidict
    
    </td>
    <td valign="top" rowspan="1">
    
    1
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    ISO 14651 ordering standard
    
    </td>
    <td valign="top" rowspan="1">
    
    14651
    
    </td>
    <td valign="top" rowspan="1">
    
    22
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    Shift-JIS binary order
    
    </td>
    <td valign="top" rowspan="1">
    
    sjisbin
    
    </td>
    <td valign="top" rowspan="1">
    
    179
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    Unicode UTF-8 binary sort
    
    </td>
    <td valign="top" rowspan="1">
    
    utf8bin
    
    </td>
    <td valign="top" rowspan="1">
    
    24
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    EUC JIS binary order
    
    </td>
    <td valign="top" rowspan="1">
    
    eucjisbn
    
    </td>
    <td valign="top" rowspan="1">
    
    192
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    GB2312 binary order
    
    </td>
    <td valign="top" rowspan="1">
    
    gb2312bn
    
    </td>
    <td valign="top" rowspan="1">
    
    137
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    CP932 MS binary order
    
    </td>
    <td valign="top" rowspan="1">
    
    cp932bin
    
    </td>
    <td valign="top" rowspan="1">
    
    129
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    Big5 binary order
    
    </td>
    <td valign="top" rowspan="1">
    
    big5bin
    
    </td>
    <td valign="top" rowspan="1">
    
    194
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    EUC KSC binary order
    
    </td>
    <td valign="top" rowspan="1">
    
    euckscbn
    
    </td>
    <td valign="top" rowspan="1">
    
    161
    
    </td>
    </tr>
    </table>
    

With respect to collation tailoring, full sensitivity is generally the intent when creating sort-keys, so when you specify a non-UCA collation, the default tailoring applied is equivalent to case=Respect. For example, the following two statements are equivalent:

```
SELECT SORTKEY( 'abc', '1252LATIN1' );
SELECT SORTKEY( 'abc', '1252LATIN1(case=Respect)' );
```

When specifying a non-UCA collation, by default, collation tailorings are accent and case-sensitive. However, for non-UCA collations, you can override only the case sensitivity using a collation tailoring. For example:

```
SELECT SORTKEY( 'abc', '1252LATIN1(case=LowerFirst)' ); 
```

If the database was created without specifying tailoring options, the following two clauses may generate different sort orders, even if the database collation name is specified for the `SORTKEY` function:

```
ORDER BY string-expression;
```

```
ORDER BY SORTKEY( string-expression, database-collation-name );
```

Different sort orders may be generated, because the default tailoring settings used for database creation and for the `SORTKEY` function are different. To get the same behavior from `SORTKEY` as for the database collation, either provide a tailoring syntax for *<collation-tailoring-string\>* that matches the settings for the database collation, or specify `db_collation` for collation-name. For example:

```
SORTKEY( expression, 'db_collation' );
```



<a name="loio66b441998f6b490ca54f8314748c9331__section_vmh_2y5_vrb"/>

## Standards and Compatibility

SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio66b441998f6b490ca54f8314748c9331__section_dx1_fy5_vrb"/>

## Example

The following statement queries the Employees table and returns the FirstName and Surname of all employees, sorted by the sort-key values for the Surname column using the dict collation \(Latin-1, English, French, German dictionary\):

```
SELECT Surname, GivenName FROM Employees ORDER BY SORTKEY( Surname, 'dict' );
```

**Related Information**  


[Collations in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_1_QRC/en-US/665704355a5147879224d7ec0aae629f.html "Data lake Relational Engine databases use CESU8BIN (CESU-8, 8-bit multibyte encoding for Unicode, binary ordering) collation and the Unicode Collation Algorithm (UCA).") :arrow_upper_right:

[SORTKEY Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a5805ddb84f2101591ffe19db63f3521.html "Generates values that can be used to sort character strings based on alternate collation rules.") :arrow_upper_right:

