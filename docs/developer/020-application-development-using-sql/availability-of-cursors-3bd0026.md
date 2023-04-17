<!-- loio3bd0026a6c5f10149c3fe2172e1f1610 -->

# Availability of Cursors

Not all interfaces provide support for all types of cursors.

-   ADO.NET supports only forward-only, read-only cursors.

-   ADO/OLE DB and ODBC support all types of cursors.

-   Embedded SQL supports all types of cursors.

-   For JDBC:

    -   The SAP IQ JDBC driver permits the declaration of insensitive, sensitive, and forward-only asensitive cursors.

    -   jConnect supports the declaration of insensitive, sensitive, and forward-only asensitive cursors in the same manner as the SAP IQ JDBC driver driver. However, the underlying implementation of jConnect only supports asensitive cursor semantics.


-   SAP Open Client supports only asensitive cursors. Also, a severe performance penalty results when using updatable, non-unique cursors.


