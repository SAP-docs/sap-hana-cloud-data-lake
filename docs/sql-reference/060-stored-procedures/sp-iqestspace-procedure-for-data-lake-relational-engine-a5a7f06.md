<!-- loioa5a7f06d84f210158e22bbecee776c23 -->

# sp\_iqestspace Procedure for Data Lake Relational Engine

Estimates the amount of space needed to create an index based on the number of rows in the table.



<a name="loioa5a7f06d84f210158e22bbecee776c23__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqestspace ( <table_name>, <#_of_rows>, <iq_page_size> );
```



<a name="loioa5a7f06d84f210158e22bbecee776c23__section_ir4_pmz_mbb"/>

## Parameters


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

A CHAR\(256\) parameter that specifies the name of the table



</dd><dt><b>

*<\#\_of\_rows\>*

</b></dt>
<dd>

An INT parameter that specifies the number of rows in the table



</dd><dt><b>

*<iq\_page\_size\>*

</b></dt>
<dd>

A SMALLINT parameter that specifies the page size defined for the data lake Relational Engine segment of the database \(must be a power of 2 between 65536 and 524288; the default is 131072\)



</dd>
</dl>



<a name="loioa5a7f06d84f210158e22bbecee776c23__iq_refbb_1561"/>

## Remarks

Displays the amount of space that a database requires based on the number of rows in the underlying database tables and on the database data lake Relational Engine page size. This procedure assumes that the database was created with the default block size for the specified data lake Relational Engine page size \(or else the estimate is incorrect\).



<a name="loioa5a7f06d84f210158e22bbecee776c23__iq_refbb_1560"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure. If you own the object referenced by the procedure, no additional privilege is required.

For objects owned by others, you need one of the following privileges:

-   CREATE ANY INDEX system privilege
-   ALTER ANY INDEX system privilege
-   CREATE ANY OBJECT system privilege
-   ALTER ANY OBJECT system privilege



## Side Effects

None

