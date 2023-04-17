<!-- loioa5b7510984f2101596dee9f059949bcd -->

# sp\_iqspaceused Procedure for Data Lake Relational Engine

Shows information about space available and space used in the data lake Relational Engine store, data lake Relational Engine temporary store, and data lake Relational Engine global and local shared temporary stores.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqspaceused (out mainKB            unsigned bigint,
               out mainKBUsed        unsigned bigint,
               out tempKB            unsigned bigint,
               out tempKBUsed        unsigned bigint,
               out shTempTotalKB     unsigned bigint,
               out shTempTotalKBUsed unsigned bigint,    
               out shTempLocalKB     unsigned bigint,    
               out shTempLocalKBUsed unsigned bigint)
```



<a name="loioa5b7510984f2101596dee9f059949bcd__section_pcj_xzn_nbb"/>

## Returns


<table>
<tr>
<th valign="top">

Column Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

mainKB



</td>
<td valign="top">

The total data lake Relational Engine main store space, in kilobytes.



</td>
</tr>
<tr>
<td valign="top">

mainKBUsed



</td>
<td valign="top">

The number of kilobytes of data lake Relational Engine main store space used by the database. Secondary multiplex nodes return '\(Null\)'.



</td>
</tr>
<tr>
<td valign="top">

tempKB



</td>
<td valign="top">

The total data lake Relational Engine temporary store space, in kilobytes.



</td>
</tr>
<tr>
<td valign="top">

tempKBUsed



</td>
<td valign="top">

The number of kilobytes of total data lake Relational Engine temporary store space in use by the database.



</td>
</tr>
<tr>
<td valign="top">

shTempTotalKB



</td>
<td valign="top">

The total data lake Relational Engine global shared temporary store space, in kilobytes.



</td>
</tr>
<tr>
<td valign="top">

shTempLocalKB



</td>
<td valign="top">

The total data lake Relational Engine local shared temporary store space, in kilobytes.



</td>
</tr>
<tr>
<td valign="top">

shTempLocalKBUsed



</td>
<td valign="top">

The number of kilobytes of data lake Relational Engine local shared temporary store space in use by the database.



</td>
</tr>
</table>



<a name="loioa5b7510984f2101596dee9f059949bcd__iq_refbb_1765"/>

## Remarks

sp\_iqspaceused returns several values as unsigned bigint out parameters. This system stored procedure can be called by user-defined stored procedures to determine the amount of main, and temporary space in use.

sp\_iqspaceused returns a subset of the information provided by sp\_iqstatus, but allows the user to return the information in SQL variables to be used in calculations.

If run on a multiplex database, this procedure applies to the server on which it runs. Also returns space used on IQ\_SHARED\_TEMP.



<a name="loioa5b7510984f2101596dee9f059949bcd__iq_refbb_1764"/>

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

-   MANAGE ANY DBSPACE
-   MONITOR



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



<a name="loioa5b7510984f2101596dee9f059949bcd__iq_refbb_1768"/>

## Example

sp\_iqspaceused requires seven output parameters. This example creates a user-defined stored procedure myspace that declares the seven output parameters, then calls sp\_iqspaceused:

```
  create or replace procedure dbo.myspace()   
begin   
     declare mt unsigned bigint;   
     declare mu unsigned bigint;   
     declare tt unsigned bigint;   
     declare tu unsigned bigint;   
     declare gt unsigned bigint;   
     declare gu unsigned bigint;   
     declare lt unsigned bigint;   
     declare lu unsigned bigint; 
     declare tt_t unsigned bigint;
     declare mt_t unsigned bigint;
     declare gt_t unsigned bigint;
     declare lt_t unsigned bigint;     
     call sp_iqspaceused(mt,mu,tt,tu,gt,gu,lt,lu);       
     if (tt = 0) then
        set tt_t = 0;
     else
        set tt_t = tu*100/tt;
     end if;
     if (mt = 0) then
        set mt_t = 0;
     else
        set mt_t = mu*100/mt;
     end if;
     if (gt = 0) then
        set gt_t = 0;
     else
        set gt_t = gu*100/gt;
     end if;
     if (lt = 0) then
        set lt_t = 0;
     else
        set lt_t = lu*100/lt;
     end if;
  select cast(mt/1024 as unsigned bigint) as mainMB,
         cast(mu/1024 as unsigned bigint) as mainusedMB, mt_t as mainPerCent,
         cast(tt/1024 as unsigned bigint) as tempMB,
         cast(tu/1024 as unsigned bigint) as tempusedMB, tt_t as tempPerCent,
         cast(gt/1024 as unsigned bigint) as shTempTotalKB,
         cast(gu/1024 as unsigned bigint) as shTempTotalKBUsed, gt_t as globalshtempPerCent,
         cast(lt/1024 as unsigned bigint) as shTempLocalMB,
         cast(lu/1024 as unsigned bigint) as shTempLocalKBUsed, lt_t as localshtempPerCent;
end
```

To display the output of sp\_iqspaceused, execute myspace:

```
myspace
```

