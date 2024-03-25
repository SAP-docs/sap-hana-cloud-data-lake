<!-- loioa5fd29ba84f210159cb498816176a030 -->

# sp\_iqshowcompression Procedure for Data Lake Relational Engine

Displays compression settings for columns of LONG BINARY \(BLOB\) and LONG VARCHAR \(CLOB\) data types.



<a name="loioa5fd29ba84f210159cb498816176a030__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqshowcompression ( <owner>, <table>, <column> )
```



<a name="loioa5fd29ba84f210159cb498816176a030__iq_iquda_120"/>

## Parameters


<dl>
<dt><b>

*<owner\>*

</b></dt>
<dd>

The owner of the table for which you are setting compression.



</dd><dt><b>

*<table\>*

</b></dt>
<dd>

The table for which you are setting compression.



</dd><dt><b>

*<column\>*

</b></dt>
<dd>

The column for which you are setting compression.



</dd>
</dl>



<a name="loioa5fd29ba84f210159cb498816176a030__iq_iquda_122"/>

## Result Set

Returns the column name and compression setting. Compression setting values are 'ON' \(compression enabled\) and 'OFF' \(compression disabled\).



<a name="loioa5fd29ba84f210159cb498816176a030__iq_iquda_121"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure along with one of the following:

-   ALTER ANY TABLE system privilege
-   ALTER ANY OBJECT system privilege



## Side Effects

None



<a name="loioa5fd29ba84f210159cb498816176a030__iq_iquda_124"/>

## Examples

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

