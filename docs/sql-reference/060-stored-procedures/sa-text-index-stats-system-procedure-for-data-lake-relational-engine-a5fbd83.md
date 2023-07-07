<!-- loioa5fbd83484f210158d6fe1b9b7331051 -->

# sa\_text\_index\_stats System Procedure for Data Lake Relational Engine

Returns statistical information about the TEXT indexes in the database.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_text_index_stats( )
```



<a name="loioa5fbd83484f210158d6fe1b9b7331051__iq_iquda_94"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`owner_id`



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

ID of the owner of the table



</td>
</tr>
<tr>
<td valign="top">

`table_id`



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

ID of the table



</td>
</tr>
<tr>
<td valign="top">

`index_id`



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

ID of the TEXT index



</td>
</tr>
<tr>
<td valign="top">

`text_config_id`



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

ID of the text configuration referenced by the TEXT index



</td>
</tr>
<tr>
<td valign="top">

`owner_name`



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Name of the owner



</td>
</tr>
<tr>
<td valign="top">

`table_name`



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Name of the table



</td>
</tr>
<tr>
<td valign="top">

`index_name`



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Name of the TEXT index



</td>
</tr>
<tr>
<td valign="top">

`text_config_name`



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Name of the text configuration object



</td>
</tr>
<tr>
<td valign="top">

`doc_count`



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Total number of indexed column values in the TEXT index



</td>
</tr>
<tr>
<td valign="top">

`doc_length`



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Total length of data in the TEXT index



</td>
</tr>
<tr>
<td valign="top">

`pending_length`



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Total length of the pending changes



</td>
</tr>
<tr>
<td valign="top">

`deleted_length`



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Total length of the pending deletions



</td>
</tr>
<tr>
<td valign="top">

`last_refresh`



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Date and time of the last refresh



</td>
</tr>
</table>



<a name="loioa5fbd83484f210158d6fe1b9b7331051__iq_iquda_95"/>

## Remarks

Use `sa_text_index_stats` to view statistical information for each TEXT index in the database.

The `pending_length`, `deleted_length`, and `last_refresh` values are NULL for IMMEDIATE REFRESH TEXT indexes.



<a name="loioa5fbd83484f210158d6fe1b9b7331051__iq_iquda_96"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with one of the following system privileges:

-   MANAGE ANY STATISTICS
-   CREATE ANY INDEX
-   ALTER ANY INDEX
-   DROP ANY INDEX
-   CREATE ANY OBJECT
-   ALTER ANY OBJECT
-   DROP ANY OBJECT



<a name="loioa5fbd83484f210158d6fe1b9b7331051__section_t1n_lss_mbb"/>

## Side Effects

None



<a name="loioa5fbd83484f210158d6fe1b9b7331051__iq_iquda_97"/>

## Example

The following example returns statistical information for each TEXT index in the database:

```
CALL sa_text_index_stats( );
```

