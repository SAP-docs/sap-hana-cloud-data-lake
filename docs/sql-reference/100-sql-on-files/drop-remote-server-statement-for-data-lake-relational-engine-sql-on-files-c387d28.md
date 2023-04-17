<!-- loioc387d28ef660402d99c7994cd8fee742 -->

# DROP \(Remote\) SERVER Statement for Data Lake Relational Engine \[SQL on Files\]

Drop a remote server from SQL on Files tables.



> ### Restriction:  
> This topic is limited to SQL on Files use cases.
> 
> This SQL on Files SQL statement can be used when connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioc387d28ef660402d99c7994cd8fee742__section_k3l_nz3_bpb"/>

## Syntax

```
DROP SERVER <server-name>
```



<a name="loioc387d28ef660402d99c7994cd8fee742__IQ_Usage"/>

## Remarks

Before `DROP SERVER` succeeds, drop all the virtual tables that have been defined for the remote server.



<a name="loioc387d28ef660402d99c7994cd8fee742__IQ_Permissions"/>

## Privileges

You have been granted the HDL\_FILES\_SERVICE\_ADMIN role.



<a name="loioc387d28ef660402d99c7994cd8fee742__IQ_Examples"/>

## Examples

The following example drops the server `SOF_server`:

```
DROP SERVER SOF_server
```

**Related Information**  


[CREATE REMOTE SERVER Statement for Data Lake Relational Engine \[SQL on Files\]](create-remote-server-statement-for-data-lake-relational-engine-sql-on-files-d9c56ec.md "Define a remote server using SQL on Files.")

