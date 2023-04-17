<!-- loioa5fd29ba84f210159cb498816176a030 -->

# sp\_iqshowcompression Procedure for Data Lake Relational Engine

Displays compression settings for columns of LONG BINARY \(BLOB\) and LONG VARCHAR \(CLOB\) data types.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqshowcompression ( <owner>, <table>, <column> )
```



<a name="loioa5fd29ba84f210159cb498816176a030__iq_iquda_120"/>

## Parameters

 *<owner\>*
 :   The owner of the table for which you are setting compression.

  *<table\>*
 :   The table for which you are setting compression.

  *<column\>*
 :   The column for which you are setting compression.

 

<a name="loioa5fd29ba84f210159cb498816176a030__iq_iquda_122"/>

## Returns

Returns the column name and compression setting. Compression setting values are 'ON' \(compression enabled\) and 'OFF' \(compression disabled\).



<a name="loioa5fd29ba84f210159cb498816176a030__iq_iquda_121"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). 

You also need one of the following:


<table>
<tr>
<th valign="top">

Privilege Name



</th>
<th valign="top">

Privilege Type



</th>
<th valign="top">

Grant Statement



</th>
</tr>
<tr>
<td valign="top">

-   ALTER ANY TABLE
-   ALTER ANY OBJECT



</td>
<td valign="top">

System privileges



</td>
<td valign="top">

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md)



</td>
</tr>
</table>



## Side Effects

None



<a name="loioa5fd29ba84f210159cb498816176a030__iq_iquda_124"/>

## Example

Assume this table definition:

```
CREATE TABLE USR.pixTable (picID INT NOT NULL,
picJPG LONG BINARY NOT NULL);
```

To check the compression status of the columns in the pixTable table, call sp\_iqshowcompression:

```
CALL sp_iqshowcompression('USR', 'pixTable',
'picJPG') ;
```

This command returns one row:

```
'picJPG','ON'
```

