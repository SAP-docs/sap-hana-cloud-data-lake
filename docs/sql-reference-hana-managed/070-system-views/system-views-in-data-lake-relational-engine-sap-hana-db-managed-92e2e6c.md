<!-- loio92e2e6c466d844e0b0e961069aa3b8d7 -->

# System Views in Data Lake Relational Engine \(SAP HANA DB-Managed\)

System views allow you to query for information about the system state using SELECT statements. The results appear as tables.



Information from system views can only be returned using REMOTE\_EXECUTE.

System views are located in the data lake Relational Engine SYS schema. You create a view that selects from the system view. The system then automatically creates an SAP HANA database virtual table with the same name as the data lake Relational Engine view in the SAP HANA database relational container schema. You query the virtual table to display the information.

