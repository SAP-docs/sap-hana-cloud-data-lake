<!-- loioa59dae3484f21015bb068d7476af8cf5 -->

# sp\_iqcheckoptions Procedure for Data Lake Relational Engine

For the connected user, sp\_iqcheckoptions displays a list of the current value and the default value of database and server startup options that have been changed from the default.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqcheckoptions
```



<a name="loioa59dae3484f21015bb068d7476af8cf5__section_qnq_syz_mbb"/>

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

User\_name



</td>
<td valign="top">

The name of the user or role for whom the option has been set. At database creation, all options are set for the PUBLIC role. Any option that has been set for a role or user other than PUBLIC is displayed.



</td>
</tr>
<tr>
<td valign="top">

Option\_name



</td>
<td valign="top">

The name of the option.



</td>
</tr>
<tr>
<td valign="top">

Current\_value



</td>
<td valign="top">

The current value of the option.



</td>
</tr>
<tr>
<td valign="top">

Default\_value



</td>
<td valign="top">

The default value of the option.



</td>
</tr>
<tr>
<td valign="top">

Option\_type



</td>
<td valign="top">

“Temporary” for a TEMPORARY option, else “Permanent”.



</td>
</tr>
</table>



<a name="loioa59dae3484f21015bb068d7476af8cf5__iq_refbb_1436"/>

## Remarks

Returns one row for each option that has been changed from the default value. The output is sorted by option name, then by user name.

For the connected user, the sp\_iqcheckoptions stored procedure displays a list of the current value and the default value of database and server startup options that have been changed from the default. sp\_iqcheckoptions considers all data lake Relational Engine and SAP SQL Anywhere database options. Data lake Relational Engine modifies some SAP SQL Anywhere option defaults, and these modified values become the new default values. Unless the new data lake Relational Engine default value is changed again, sp\_iqcheckoptions does not list the option.

When sp\_iqcheckoptions is run, the HDLADMIN user sees all options set on a permanent basis for all roles and users and sees temporary options set for the DBA. Users who are not DBAs see their own temporary options. All users see nondefault server startup options.

The HDLADMIN user sees all options set on a permanent basis for all roles and users, along with temporary options set for the DBA. Users who are not DBAs see their own temporary options. All users see nondefault server startup options.



<a name="loioa59dae3484f21015bb068d7476af8cf5__iq_refbb_1434"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None



<a name="loioa59dae3484f21015bb068d7476af8cf5__iq_refbb_1438"/>

## Examples

In these examples, the temporary option APPEND\_LOAD is set to ON and the role myrole has the option MAX\_WARNINGS set to 9. The user joel has a temporary value of 55 set for MAX\_WARNINGS.

-   In the first example, sp\_iqcheckoptions is run by user HDLADMIN:

    ```
    User_name        Option_name          Current_value           Default_value   Option_type
    HDLADMIN         Ansi_update_constr   CURSORS                 Off             Permanent
    PUBLIC           Ansi_update_constr   Cursors                 Off             Permanent
    HDLADMIN         Checkpoint_time      20                      60              Temporary
    HDLADMIN         Connection_authent   Company=MyComp;                         Temporary
                                          Application=DBTools;Signa 
    HDLADMIN         Login_procedure      HDLADMIN.sp_iq_proce    sp_login_envir  Permanent
    PUBLIC           Login_procedure      HDLADMIN.sp_iq_proce    sp_login_envir  Permanent
    myrole           Max_Warnings         9                       281474976710655 Permanent
    HDLADMIN         Thread_count         25                      0               Temporary
    ```

-   In the second example, sp\_iqcheckoptions is run by the user joel:

    ```
    User_name Option_name          Current_value           Default_value   Option_type
    joel      Ansi_update_constr   CURSORS                 Off             Permanent
    PUBLIC    Ansi_update_constr   Cursors                 Off             Permanent
    joel      Checkpoint_time      20                      60              Temporary
    joel      Connection_authent   Company=MyComp;                         Temporary
                                   Application=DBTools;Signa 
    joel      Login_procedure      HDLADMIN.sp_iq_proce    sp_login_envir  Permanent
    PUBLIC    Login_procedure      HDLADMIN.sp_iq_proce    sp_login_envir  Permanent
    joel      Max_Warnings         55                      281474976710655 Temporary
    joel      Thread_count         25                      0               Temporary
    ```


