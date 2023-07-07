<!-- loiobc2b06da6caf497f9601f2d2d6e9e063 -->

# OPENXML Operator in Data Lake Relational Engine \(SAP HANA DB-Managed\)

A string operator that generates a result set from an XML document.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) syntax can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.



**Syntax 1 - Specify the XML**

```
OPENXML(
   <xml-data>, <xpath>
   [, <flags>
   [, <namespaces> ] ]
   )
   WITH (
   <column-name> <column-type> 
   [ <xpath> , ... ]
   )
```

**Syntax 2 - Specify a File Containing the XML**

```
OPENXML(
   { USING FILE | USING VALUE } <xml-data>, <xpath>
   [, <flags>
   [, <namespaces> ] ]
   )
   WITH ( <column-name> <column-type>
   [ <xpath> , ... ]
   ) 
   [ OPTION ( <scan-option> ) ]
   [ AS ] <correlation-name>
```

```
<scan-option> :
   { ENCODING <encoding>
   | BYTE ORDER MARK { ON | OFF } }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiobc2b06da6caf497f9601f2d2d6e9e063__section_wtq_kkl_bwb"/>

## Parameters


<dl>
<dt><b>

WITH clause

</b></dt>
<dd>

Specifies the schema of the result set and how the value is found for each column in the result set. WITH clause *<xpath\>* arguments are matched relative to the matches for the *<xpath\>* in the second argument. If a WITH clause expression matches more than one node, then only the first node in the document order is used. If the node is not a text node, then the result is found by appending all the text node descendants. If a WITH clause expression does not match any nodes, then the column for that row is NULL.

The *<xpath\>* arguments in the WITH clause can be literal strings or variables. See [http://www.w3.org/TR/xpath](http://www.w3.org/TR/xpath).

The OPENXML WITH clause syntax is similar to the syntax for selecting from a stored procedure.



</dd><dt><b>

USING FILE | USING VALUE

</b></dt>
<dd>

Use the USING FILE clause to load data from a file.

Use the USING VALUE clause to load data from any expression of CHAR, NCHAR, BINARY, or LONG BINARY type, or BLOB string.


<dl>
<dt><b>

 *<xml-data\>* 

</b></dt>
<dd>

The XML on which the result set is based. This can be any string expression, such as a constant, variable, or column.

The *<xml-data\>* is parsed directly in the NCHAR encoding if there are any NCHAR columns in the output. The xpath and namespaces arguments are also converted and parsed in the NCHAR encoding.



</dd><dt><b>

 *<xpath\>* 

</b></dt>
<dd>

A string containing an XPath query. XPath allows you to specify patterns that describe the structure of the XML document you are querying. The XPath pattern included in this argument selects the nodes from the XML document. Each node that matches the XPath query in the second *<xpath\>* argument generates one row in the table.

Metaproperties can only be specified in WITH clause *<xpath\>* arguments. A metaproperty is accessed within an XPath query as if it was an attribute. If a *<namespaces\>* is not specified, then by default the prefix mp is bound to the Uniform Resource Identifier \(URI\) urn:sap-com:sa-xpath-metaprop. If a *<namespaces\>* is specified, then this URI must be bound to mp or some other prefix to access metaproperties in the query. Metaproperty names are case-sensitive. The OPENXML statement supports the following metaproperties:


<dl>
<dt><b>

@mp:id

</b></dt>
<dd>

returns an ID for a node that is unique within the XML document. The ID for a given node in a given document may change if the database server is restarted. The value of this metaproperty increase with document order.



</dd><dt><b>

@mp:localname

</b></dt>
<dd>

returns the local part of the node name, or NULL if the node does not have a name.



</dd><dt><b>

@mp:prefix

</b></dt>
<dd>

returns the prefix part of the node name, or NULL if the node does not have a name or if the name is not prefixed.



</dd><dt><b>

@mp:namespaceuri

</b></dt>
<dd>

returns the URI of the namespace that the node belongs to, or NULL if the node is not in a namespace.



</dd><dt><b>

@mp:xmltext

</b></dt>
<dd>

returns a subtree of the XML document in XML form. For example, when you match an internal node, you can use this metaproperty to return an XML string, rather than the concatenated values of the descendant text nodes.



</dd>
</dl>



</dd><dt><b>

 *<flags\>* 

</b></dt>
<dd>

Indicates the mapping that should be used between the XML data and the result set when an XPath query is not specified in the WITH clause. If the *<flags\>* parameter is not specified, then the default behavior is to map attributes to columns in the result set. The *<flags\>* parameter can have one of the following values:


<table>
<tr>
<th valign="top">

Value



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

XML attributes are mapped to columns in the result set \(the default\).



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

XML elements are mapped to columns in the result set.



</td>
</tr>
</table>



</dd><dt><b>

 *<namespace-declaration\>* 

</b></dt>
<dd>

An XML document. The in-scope namespaces for the query are taken from the root element of the document. If namespaces are specified, then you must include a *<flags\>* argument, even if all the *<xpath\>* arguments are specified.



</dd>
</dl>



</dd><dt><b>

 *<column-name\>* 

</b></dt>
<dd>

The name of the column in the result set.



</dd><dt><b>

 *<column-type\>* 

</b></dt>
<dd>

The data type of the column in the result set. The data type must be compatible with the values selected from the XML document.



</dd><dt><b>

OPTION clause

</b></dt>
<dd>

Use the OPTION clause to specify parsing options to use for the input file, such as escape characters, delimiters, encoding, and so on.


<dl>
<dt><b>

ENCODING clause

</b></dt>
<dd>

The ENCODING clause allows you to specify the encoding that is used to read the file.

If the ENCODING clause is not specified, then encoding for values is assumed to be in the database character set \(db\_charset\) if the values are of type CHAR or BINARY, and NCHAR database character set \(nchar\_charset\) if the values are of type NCHAR.



</dd><dt><b>

BYTE ORDER MARK clause

</b></dt>
<dd>

Use the BYTE ORDER MARK clause to specify whether a byte order mark \(BOM\) is present in the encoding. By default, this option is ON, which enables the server to search for and interpret a byte order mark \(BOM\) at the beginning of the data. If BYTE ORDER MARK is OFF, then the server does not search for a BOM.

You must specify the BYTE ORDER MARK clause if the input data is encoded.

If the ENCODING clause is specified:

-   If the BYTE ORDER MARK option is ON and you specify a UTF-16 encoding with an endian such as UTF-16BE or UTF-16LE, then the database server searches for a BOM at the beginning of the data. If a BOM is present, then it is used to verify the endianness of the data. If you specify the wrong endian, then an error is returned.

-   If the BYTE ORDER MARK option is ON and you specify a UTF-16 encoding without an explicit endian, then the database server searches for a BOM at the beginning of the data. If a BOM is present, then it is used to determine the endianness of the data. Otherwise, the operating system endianness is assumed.

-   If the BYTE ORDER MARK option is ON and you specify a UTF-8 encoding, then the database server searches for a BOM at the beginning of the data. If a BOM is present, then it is ignored.


If the ENCODING clause is not specified:

-   If you do not specify an ENCODING clause and the BYTE ORDER MARK option is ON, then the server looks for a BOM at the beginning of the input data. If a BOM is located, then the source encoding is automatically selected based on the encoding of the BOM \(UTF-16BE, UTF-16LE, or UTF-8\) and the BOM is not considered to be part of the data to be loaded.

-   If you do not specify an ENCODING clause and the BYTE ORDER MARK option is OFF, or a BOM is not found at the beginning of the input data, then the database CHAR encoding is used.




</dd>
</dl>



</dd>
</dl>



<a name="loiobc2b06da6caf497f9601f2d2d6e9e063__section_bpj_lkl_bwb"/>

## Remarks

The OPENXML operator parses the *<xml-data\>* and models the result as a tree. The tree contains a separate node for each element, attribute, and text node, or other XML construct. The XPath queries supplied to the OPENXML operator are used to select nodes from the tree, and the selected nodes are then mapped to the result set.

The XML parser used by the OPENXML operator is nonvalidating, and does not read the external DTD subset or external parameter entities.

If disk sandboxing is enabled, then database operations are limited to the directory where the main database file is located.

When there are multiple matches for a column expression, the first match in the document order \(the order of the original XML document before it was parsed\) is used. NULL is returned if there are no matching nodes. When an internal node is selected, the result is all the descendant text nodes of the internal node concatenated together.

Columns of type BINARY, LONG BINARY, IMAGE, and VARBINARY are assumed to be in base64-encoded format and are decoded automatically. If you generate XML using the FOR XML clause, then these types are base64-encoded, and can be decoded using the OPENXML operator.

The OPENXML operator supports a subset of the XPath syntax, as follows:

-   The child, self, attribute, descendant, descendant-or-self, and parent axes are fully supported.

-   Both abbreviated and unabbreviated syntax can be used for all supported features. For example, 'a' is equivalent to 'child::a' and '..' is equivalent to 'parent::node\(\)'.

-   Name tests can use wildcards. For example, 'a/\*/b'.

-   The following kind tests are supported: node\(\), text\(\), processing-instruction\(\), and comment\(\).

-   Qualifiers of the form *<expr1\>*\[*<expr2\>*\] and *<expr1\>*\[*<expr2\>*="*<string\>*" \] can be used, where *<expr2\>* is any supported XPath expression. A qualifier evaluates TRUE if *<expr2\>* matches one or more nodes. For example, 'a\[b\]' finds a nodes that have at least one b child, and a\[b="I"\] finds a nodes that have at least one b child with a text value of I.




<a name="loiobc2b06da6caf497f9601f2d2d6e9e063__IQ_Permissions"/>

## Privileges

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loiobc2b06da6caf497f9601f2d2d6e9e063__section_e2c_vnl_bwb"/>

## Example

The following query generates a result set from the XML document supplied as the first argument to the OPENXML operator:

```
SELECT * FROM OPENXML( '<products>
                 <ProductType ID="301">Tee Shirt</ProductType>
                 <ProductType ID="401">Baseball Cap</ProductType>
                 </products>',
                 '/products/ProductType' )
WITH ( ProductName LONG VARCHAR 'text()', ProductID CHAR(3) '@ID');
```

This query generates the following result:


<table>
<tr>
<th valign="top">

ProductName



</th>
<th valign="top">

ProductID



</th>
</tr>
<tr>
<td valign="top">

Tee Shirt



</td>
<td valign="top">

301



</td>
</tr>
<tr>
<td valign="top">

Baseball Cap



</td>
<td valign="top">

401



</td>
</tr>
</table>

In the following example, the first <ProductType\> element contains an entity. When you execute the query, this node is parsed as an element with four children: Tee, &amp;, Sweater, and Set. You can use a period \(.\) to concatenate the children together in the result set.

```
SELECT * FROM OPENXML( '<products>
                 <ProductType ID="301">Tee &amp; Sweater Set</ProductType>
                 <ProductType ID="401">Baseball Cap</ProductType>
                 </products>',
                 '/products/ProductType' )
WITH ( ProductName LONG VARCHAR '.', ProductID CHAR(3) '@ID');
```

This query generates the following result:


<table>
<tr>
<th valign="top">

ProductName



</th>
<th valign="top">

ProductID



</th>
</tr>
<tr>
<td valign="top">

Tee & Sweater Set



</td>
<td valign="top">

301



</td>
</tr>
<tr>
<td valign="top">

Baseball Cap



</td>
<td valign="top">

401



</td>
</tr>
</table>

The following query uses an equality predicate to generate a result set from the supplied XML document.

```
SELECT * FROM OPENXML('<EmployeeDirectory>
   <Employee>
      <column name="EmployeeID">105</column>
      <column name="GivenName">Matthew</column>
      <column name="Surname">Cobb</column>
      <column name="Street">7 Pleasant Street</column>
      <column name="City">Grimsby</column>
      <column name="State">UT</column>
      <column name="PostalCode">02154</column>
      <column name="Phone">6175553840</column>
   </Employee>
  <Employee>
      <column name="EmployeeID">148</column>
      <column name="GivenName">Julie</column>
      <column name="Surname">Jordan</column>
      <column name="Street">1244 Great Plain Avenue</column>
      <column name="City">Woodbridge</column>
      <column name="State">AZ</column>
      <column name="PostalCode">01890</column>
      <column name="Phone">6175557835</column>
   </Employee>
  <Employee>
      <column name="EmployeeID">160</column>
      <column name="GivenName">Robert</column>
      <column name="Surname">Breault</column>
      <column name="Street">358 Cherry Street</column>
      <column name="City">Milton</column>
      <column name="State">PA</column>
      <column name="PostalCode">02186</column>
      <column name="Phone">6175553099</column>
   </Employee>
  <Employee>
      <column name="EmployeeID">243</column>
      <column name="GivenName">Natasha</column>
      <column name="Surname">Shishov</column>
      <column name="Street">151 Milk Street</column>
      <column name="City">Grimsby</column>
      <column name="State">UT</column>
      <column name="PostalCode">02154</column>
      <column name="Phone">6175552755</column>
   </Employee> 
</EmployeeDirectory>', '/EmployeeDirectory/Employee')
WITH ( EmployeeID INT 'column[@name="EmployeeID"]',
       GivenName    CHAR(20) 'column[@name="GivenName"]',
       Surname      CHAR(20) 'column[@name="Surname"]',
       PhoneNumber  CHAR(10) 'column[@name="Phone"]');
```

This query generates the following result set:


<table>
<tr>
<th valign="top">

EmployeeID



</th>
<th valign="top">

GivenName



</th>
<th valign="top">

Surname



</th>
<th valign="top">

PhoneNumber



</th>
</tr>
<tr>
<td valign="top">

105



</td>
<td valign="top">

Matthew



</td>
<td valign="top">

Cobb



</td>
<td valign="top">

6175553840



</td>
</tr>
<tr>
<td valign="top">

148



</td>
<td valign="top">

Julie



</td>
<td valign="top">

Jordan



</td>
<td valign="top">

6175557835



</td>
</tr>
<tr>
<td valign="top">

160



</td>
<td valign="top">

Robert



</td>
<td valign="top">

Breault



</td>
<td valign="top">

6175553099



</td>
</tr>
<tr>
<td valign="top">

243



</td>
<td valign="top">

Natasha



</td>
<td valign="top">

Shishov



</td>
<td valign="top">

6175552755



</td>
</tr>
</table>

The following query uses the XPath @attribute expression to generate a result set:

```
SELECT * FROM OPENXML( '<Employee
      EmployeeID="105"
      GivenName="Matthew"
      Surname="Cobb"
      Street="7 Pleasant Street"
      City="Grimsby"
      State="UT"
      PostalCode="02154"
      Phone="6175553840"
      />', '/Employee' )
WITH ( EmployeeID   INT      '@EmployeeID',
       GivenName    CHAR(20) '@GivenName',
       Surname      CHAR(20) '@Surname',
       PhoneNumber  CHAR(10) '@Phone');
```

The following query operates on an XML document like the one used in the above query, except that an XML namespace has been introduced. It demonstrates the use of wildcards in the name test for the XPath query, and generates the same result set as the above query.

```
SELECT * FROM OPENXML( '<Employee  xmlns="http://www.sap.com/EmployeeDemo"
      EmployeeID="105"
      GivenName="Matthew"
      Surname="Cobb"
      Street="7 Pleasant Street"
      City="Grimsby"
      State="UT"
      PostalCode="02154"
      Phone="6175553840"
/>', '/*:Employee' )

WITH ( EmployeeID   INT      '@EmployeeID',
       GivenName    CHAR(20) '@GivenName',
       Surname      CHAR(20) '@Surname',
       PhoneNumber  CHAR(10) '@Phone');
```

Alternatively, you could specify a namespace declaration:

```
SELECT * FROM OPENXML( '<Employee xmlns="http://www.sap.com/EmployeeDemo"
      EmployeeID="105"
      GivenName="Matthew"
      Surname="Cobb"
      Street="7 Pleasant Street"
      City="Grimsby"
      State="UT"
      PostalCode="02154"
      Phone="6175553840"
/>', '/prefix:Employee', 1, '<r xmlns:prefix="http://www.sap.com/EmployeeDemo"/>' )
WITH ( EmployeeID   INT      '@EmployeeID',
       GivenName    CHAR(20) '@GivenName',
       Surname      CHAR(20) '@Surname',
       PhoneNumber  CHAR(10) '@Phone');
```

The following example illustrates the USING FILE syntax.

```
SELECT Products.* FROM OPENXML( USING FILE 'products.xml', '/products/ProductType' ) 
WITH ( ProductName LONG VARCHAR 'text()', ProductID CHAR(3) '@ID' ) AS Products;
```

The products.xml file contains the following XML text.

```
<products>
<ProductType ID="301">Tee Shirt</ProductType>
<ProductType ID="401">Baseball Cap</ProductType>
</products>
```

This query generates the following result:


<table>
<tr>
<th valign="top">

ProductName



</th>
<th valign="top">

ProductID



</th>
</tr>
<tr>
<td valign="top">

Tee Shirt



</td>
<td valign="top">

301



</td>
</tr>
<tr>
<td valign="top">

Baseball Cap



</td>
<td valign="top">

401



</td>
</tr>
</table>

The following example illustrates the USING VALUE syntax.

```
CREATE OR REPLACE VARIABLE xmltext LONG VARCHAR =
'<feed>
  <title>Example Feed</title>
  <link href="http://example.org/"/>
  <updated>2017-04-27T14:30:04Z</updated>
  <author>
    <name>John Doe</name>
  </author>
  <id>urn:uuid:60a76c80-d399-11d9-b93C-0003939e0af6</id>
  <entry>
    <title>Atom-Powered Robots Run Amok</title>
    <link href="http://example.org/2016/12/13/atom03"/>
    <id>urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a</id>
    <updated>2016-12-13T18:30:02Z</updated>
    <summary>Some text.</summary>
  </entry>
  <entry>
    <title>More Atom-Powered Robots Run Amok</title>
    <link href="http://example.org/2017/04/27/atom04"/>
    <id>urn:uuid:1325c695-cfb8-4ebb-aaaa-80da344efa6a</id>
    <updated>2017-04-27T13:29:12Z</updated>
    <summary>Some more text.</summary>
  </entry>
</feed>';

SELECT * FROM OPENXML( USING VALUE xmltext, '/feed/entry' )
WITH ( Title        LONG VARCHAR '../title',
       Link         LONG VARCHAR '../link/@href',
       Updated      LONG VARCHAR '../updated',
       Author       LONG VARCHAR '../author/name',
       Ident        LONG VARCHAR '../id',
       EntryTitle   LONG VARCHAR 'title',
       EntryLink    LONG VARCHAR 'link/@href',
       EntryId      LONG VARCHAR 'id',
       EntryUpdated LONG VARCHAR 'updated',
       EntrySummary LONG VARCHAR 'summary') AS F;
```

This query generates a result with two rows.

