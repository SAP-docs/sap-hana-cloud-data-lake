<!-- loio7b768a5d681f4b35a2b1bbcd78ae04aa -->

# UNPIVOT Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Unpivots compatible-type columns of a table expression in a FROM clause \(FROM *<unpivoted-derived-table expression\>*\) into rows in a derived table. Unpivoting is used to normalize data, for example when you have similar data stored in multiple columns in tables and you want to return it in one column.



<a name="loio7b768a5d681f4b35a2b1bbcd78ae04aa__window_clause_usage1"/>

## Usage

This SQL statement clause can only be used within the FROM clause in a SELECT statement.



```
FROM <unpivoted-derived-table>

<unpivoted-derived-table> : 
<unpivot-source-table> UNPIVOT [ { INCLUDE | EXCLUDE } NULLS ]  ( <unpivot-clause> ) [ AS ] <correlation-name>

<unpivot-clause> : 
<unpivot-value-clause> <unpivot-for-clause> <unpivot-in-clause>

<unpivot-value-clause> : 
<value-column>
| ( <value-column> [,...] ) 

<unpivot-for-clause> : 
FOR <unpivot-column> 

<unpivot-in-clause> : 
IN ( <unpivot-old-column> [[ AS ] <unpivot-old-column-alias> ] [,...] )
| IN ( ( <unpivot-old-column> [,...] ) [[ AS ] <unpivot-old-column-alias> ] [,...] )
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio7b768a5d681f4b35a2b1bbcd78ae04aa__section_o31_sjp_njb"/>

## Parameters


<dl class="glossary">
<dt><b>

\{ INCLUDE | EXCLUDE \} NULLS

</b></dt>
<dd>

Specify whether to include or exclude NULL values in the results for *<value-column\>*. The default behavior is EXCLUDE NULLS.



</dd><dt><b>

*<unpivot-value-clause\>*

</b></dt>
<dd>

Specify name\(s\) for the new columns in the unpivoted derived table that will hold unpivoted values.



</dd><dt><b>

*<unpivot-for-clause\>*

</b></dt>
<dd>

Specify a column to unpivot the data for.



</dd><dt><b>

*<unpivot-in-clause\>*

</b></dt>
<dd>

Specify the values of *<unpivot-for-clause\>* to unpivot data for.



</dd>
</dl>



<a name="loio7b768a5d681f4b35a2b1bbcd78ae04aa__section_p31_sjp_njb"/>

## Remarks

An unpivoted derived table contains a subset of the columns in *<unpivot-source-table\>*, plus additional columns specified in the *<unpivot-value-clause\>* and *<unpivot-column\>*. The columns in the IN clause must be found in *<unpivot-source-table\>* but aren’t present in the unpivoted derived table.

If the IN clause has *<I\>* elements, then each row in *<unpivot-source-table\>* is transformed into *<I\>* rows in the unpivoted derived table. That is, each value tuple corresponding to an item in the IN clause generates a new row in the unpivoted derived table. The *<unpivot-column\>* value for each row is set to the value of the IN clause alias for that item. The new columns specified in *<unpivot-value-clause\>* are set to the value tuple of the original row for that item.

Each item in the IN clause requires compatible domains with any other items in the IN clause. The data type for the new columns specified in *<unpivot-value-clause\>* corresponds to a super type of these compatible domains. The data type of the values in *<unpivot-column\>* is NCHAR, and its values are the aliases defined in the IN clause.



<a name="loio7b768a5d681f4b35a2b1bbcd78ae04aa__section_r31_sjp_njb"/>

## Side Effects

None.



<a name="loio7b768a5d681f4b35a2b1bbcd78ae04aa__section_s31_sjp_njb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



## Example

Suppose that you have a table called MyCustomers, containing the names of your contacts and the various phone numbers they have. The following statements create such a table, populate it with fictitious data, and then query the table:

```

CREATE TABLE MyCustomers
( ContactID INT PRIMARY KEY, 
  LastName VARCHAR(64),
  FirstName VARCHAR(64),
  Home VARCHAR(32),
  Mobile VARCHAR(32),
  AltPhone VARCHAR(32)
);
INSERT MyCustomers
  ( ContactID, LastName, FirstName, Home, Mobile, AltPhone )
VALUES
  ( 1, 'Bringle', 'Susan', '111-593-1451', '222-693-7620', NULL ),
  ( 2, 'Hoffsteter', 'Garth', '113-249-6622', NULL, NULL),
  ( 3, 'Zenibar', 'Austin', NULL, '171-765-8730', '888-536-5324' );
SELECT * FROM MyCustomers;
```


<table>
<tr>
<th valign="top">

ContactID

</th>
<th valign="top">

LastName

</th>
<th valign="top">

FirstName

</th>
<th valign="top">

Home

</th>
<th valign="top">

Mobile

</th>
<th valign="top">

AltPhone

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

Bringle

</td>
<td valign="top">

Susan

</td>
<td valign="top">

111-593-1451

</td>
<td valign="top">

222-693-7620

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

Hoffsteter

</td>
<td valign="top">

Garth

</td>
<td valign="top">

113-249-6622

</td>
<td valign="top">

\(NULL\)

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

Zenibar

</td>
<td valign="top">

Austin

</td>
<td valign="top">

\(NULL\)

</td>
<td valign="top">

171-765-8730

</td>
<td valign="top">

888-555-5555

</td>
</tr>
</table>

For each contact, the contact numbers are stored in three separate columns: Home, Mobile, and AltPhone.

Now, suppose that you need to gather some statistics related to phone numbers that your customer service representatives call. You want to see a list of all phone numbers that are called, with the numbers sorted so that you can identify trends such as similar exchange numbers. To get the results you need, you must unpivot the Home, Mobile, and AltPhone columns into a single column that contains one row per phone number, sorted by phone number. Your SELECT statement could look as follows:

```
SELECT ContactID, PhoneNumber, PhoneType
FROM
(
  SELECT ContactID, Home, Mobile, AltPhone 
  FROM MyCustomers
) AS MyUnpivotSource
UNPIVOT EXCLUDE NULLS 
(
  PhoneNumber FOR PhoneType IN ( Home, Mobile, AltPhone )
) 
AS MyUnpivotedTable 
ORDER BY PhoneNumber;
```


<table>
<tr>
<th valign="top">

ContactID

</th>
<th valign="top">

PhoneNumber

</th>
<th valign="top">

PhoneType

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

111-593-1451

</td>
<td valign="top">

Home

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

113-249-6622

</td>
<td valign="top">

Home

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

171-765-873

</td>
<td valign="top">

Mobile

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

222-693-7620

</td>
<td valign="top">

Mobile

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

888-536-5324

</td>
<td valign="top">

AltPhone

</td>
</tr>
</table>

The results show how the UNPIVOT operation normalizes the three columns of phone number data found in the MyCustomers table, placing them into a single phone number column called PhoneNumber, which is *<unpivot-value-clause\>* in this example. The values in the PhoneType column, which is *<unpivot-column\>* in this example, are determined by the column in which the phone number value was found in *<unpivot-source-table\>*.

The following query extracts the phone numbers for contacts and their customers in the Customers table into an unpivoted derived table where the phones are listed, and the provenance - customer phone or contact phone - is recorded in the unpivot column People.

```
SELECT DISTINCT * 
FROM 
 ( SELECT CO.CustomerID, 
          C.City customer_city, 
          C.State customer_state, 
          c.Phone customer_phone,
          CO.City contact_city, 
          CO.State contact_state, 
          CO.Phone contact_phone
   FROM Customers C 
   JOIN Contacts CO 
   WHERE  C.State IN ( 'NJ', 'NY' ) ) UnpivotSourceTable
UNPIVOT
 ( ( City, State, Phone ) FOR People IN 
     ( 
       ( customer_city, customer_state, customer_phone ) AS CustomerPhone, 
       ( contact_city, contact_state, contact_phone ) AS ContactPhone 
     )
 ) UnpivotedDerivedTable
ORDER BY CustomerID, People;
```

For example, the unpivot source table UnpivotSourceTable contains the following row \(among others\):


<table>
<tr>
<th valign="top">

CustomerID

</th>
<th valign="top">

customer\_city

</th>
<th valign="top">

customer\_state

</th>
<th valign="top">

customer\_phone

</th>
<th valign="top">

contact\_city

</th>
<th valign="top">

contact\_state

</th>
<th valign="top">

contact\_phone

</th>
</tr>
<tr>
<td valign="top">

101

</td>
<td valign="top">

Kingston

</td>
<td valign="top">

NJ

</td>
<td valign="top">

2015558966

</td>
<td valign="top">

Hespeler

</td>
<td valign="top">

NJ

</td>
<td valign="top">

6035550988

</td>
</tr>
</table>

The query unpivots the data into new rows identified by CustomerID 101 in the following result set table.


<table>
<tr>
<th valign="top">

CustomerID

</th>
<th valign="top">

People

</th>
<th valign="top">

City

</th>
<th valign="top">

State

</th>
<th valign="top">

Phone

</th>
</tr>
<tr>
<td valign="top">

101

</td>
<td valign="top">

ContactPhone

</td>
<td valign="top">

Hespeler

</td>
<td valign="top">

NJ

</td>
<td valign="top">

6035550988

</td>
</tr>
<tr>
<td valign="top">

101

</td>
<td valign="top">

CustomerPhone

</td>
<td valign="top">

Kingston

</td>
<td valign="top">

NJ

</td>
<td valign="top">

2015558966

</td>
</tr>
<tr>
<td valign="top">

111

</td>
<td valign="top">

ContactPhone

</td>
<td valign="top">

Cornwall

</td>
<td valign="top">

NY

</td>
<td valign="top">

6175557956

</td>
</tr>
<tr>
<td valign="top">

111

</td>
<td valign="top">

ContactPhone

</td>
<td valign="top">

Cornwall

</td>
<td valign="top">

NY

</td>
<td valign="top">

6175558890

</td>
</tr>
<tr>
<td valign="top">

111

</td>
<td valign="top">

CustomerPhone

</td>
<td valign="top">

Hastings

</td>
<td valign="top">

NY

</td>
<td valign="top">

3155554486

</td>
</tr>
<tr>
<td valign="top">

116

</td>
<td valign="top">

ContactPhone

</td>
<td valign="top">

Cornwall

</td>
<td valign="top">

NY

</td>
<td valign="top">

6175552222

</td>
</tr>
<tr>
<td valign="top">

116

</td>
<td valign="top">

ContactPhone

</td>
<td valign="top">

Cornwall

</td>
<td valign="top">

NY

</td>
<td valign="top">

6175559877

</td>
</tr>
<tr>
<td valign="top">

116

</td>
<td valign="top">

CustomerPhone

</td>
<td valign="top">

Stayner

</td>
<td valign="top">

NY

</td>
<td valign="top">

9145553817

</td>
</tr>
<tr>
<td valign="top">

147

</td>
<td valign="top">

ContactPhone

</td>
<td valign="top">

Hespeler

</td>
<td valign="top">

NJ

</td>
<td valign="top">

6035551200

</td>
</tr>
<tr>
<td valign="top">

147

</td>
<td valign="top">

CustomerPhone

</td>
<td valign="top">

Campbellford

</td>
<td valign="top">

NJ

</td>
<td valign="top">

9085556021

</td>
</tr>
</table>

