<!-- loioa5c4fafd84f21015967fa8d43accdd24 -->

# Procedures Supported by SAP SQL Anywhere

Data lake Relational Engine supports SAP SQL Anywhere system procedures.

> ### Tip:  
> SAP SQL Anywhere stored procedures do not contain "`iq`" in the procedure name.

The `sa_get_table_definition` procedure is only supported for SAP SQL Anywhere tables. If run against a data lake Relational Engine table, the procedure returns the error `not implemented for IQ tables`.

