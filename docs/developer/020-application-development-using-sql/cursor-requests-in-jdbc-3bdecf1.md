<!-- loio3bdecf176c5f10149128af700acc0937 -->

# Cursor Requests in JDBC

The SAP IQ JDBC driver supports three types of cursors: insensitive, sensitive, and forward-only asensitive.

The SAP IQ JDBC driver supports these different cursor types for a JDBC ResultSet object. However, there are cases when the database server cannot construct an access plan with the required semantics for a given cursor type. In these cases, the database server either returns an error or substitutes a different cursor type.

