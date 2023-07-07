<!-- loio8b235c7e68b845eeb65f5efe81fb8937 -->

# REMOTE\_EXECUTE Usage Examples for Viewing System Views

To display the information from the system view, you create a data lake Relational Engine view that points to a system view and then use the system-generated SAP HANA database virtual table to see the information.



The system view SYSTAB returns information on tables and views in data lake Relational Engine. This example show how to display this information.

Create a data lake Relational Engine view named VIEW\_SYSTAB that performs a SELECT query against the stem view.

```
CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE ('
   CREATE VIEW VIEW_SYSTAB AS SELECT * FROM SYS.SYSTAB 
');
```

Data lake Relational Engine automatically creates a corresponding virtual table with the same name as the view \(VIEW\_SYSTAB\) in the SAP HANA database relational container schema SYSHDL\_CONTAINER1.

Execute a query using the virtual table to display the information.

```
SELECT * FROM SYSHDL_CONTAINER1.VIEW_SYSTAB
```

