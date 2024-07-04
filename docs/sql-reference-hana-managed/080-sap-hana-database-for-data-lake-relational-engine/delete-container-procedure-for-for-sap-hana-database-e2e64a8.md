<!-- loioe2e64a80ae2b4ee98cebc9a7dcd027ab -->

# DELETE\_CONTAINER Procedure for for SAP HANA Database

Delete a data lake Relational Engine relational container.



```
CALL SYSHDL.DELETE_CONTAINER('<relational_container_name>'); 
```



<a name="loioe2e64a80ae2b4ee98cebc9a7dcd027ab__section_dj3_45x_cjb"/>

## Parameters


<dl>
<dt><b>

*<relational\_container\_name\>*

</b></dt>
<dd>

Specifies the name of the relational container to delete.



</dd>
</dl>



<a name="loioe2e64a80ae2b4ee98cebc9a7dcd027ab__section_zhc_rnx_cjb"/>

## Description

The system procedure performs the following tasks:

-   Drops the empty data lake Relational Engine and SAP HANA database relational container default schemas.
-   Drops the SAP HANA database container administrator role for the relational container.
-   Drops the REMOTE\_EXECUTE and REMOTE\_EXECUTE\_DDL procedures.
-   Drops the SAP HANA database remote source for the relational container.
-   Drops the remote server for the relational container.
-   Drops the data lake Relational Engine relational container user.
-   Drops the data lake Relational Engine relational container.

If user-created objects exist in the relational container when the deletion is executed, an error message is returned warning that objects exist and the deletion fails. You cannot delete the SYSRDL\#CG relational container.



<a name="loioe2e64a80ae2b4ee98cebc9a7dcd027ab__section_xlt_rnx_cjb"/>

## Privileges

You are a member of the container group administrator role \(SYSHDL\_ROLE\).



<a name="loioe2e64a80ae2b4ee98cebc9a7dcd027ab__section_f5l_5nx_cjb"/>

## Example

The following example deletes relational container CONTAINER1.

```
CALL SYSHDL.DELETE_CONTAINER('CONTAINER1');
```

**Related Information**  


[Manage Relational Containers in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_3_QRC/en-US/0b494fedebb243fc9bd92c87bac7ddd4.html "Relational containers are managed from the SAP HANA database instance, but are stored in the data lake Relational Engine instance.") :arrow_upper_right:

[Deleting a Relational Container in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_3_QRC/en-US/047e3ffb996f45d4945310e2b64efd2f.html "Delete a relational container in the container group.") :arrow_upper_right:

