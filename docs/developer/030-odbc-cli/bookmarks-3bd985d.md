<!-- loio3bd985de6c5f10148a45a47e7fe8cdbd -->

# Bookmarks

ODBC provides **bookmarks**, which are values used to identify rows in a cursor. The ODBC driver supports bookmarks for value-sensitive and insensitive cursors. For example, the ODBC cursor types SQL\_CURSOR\_STATIC and SQL\_CURSOR\_KEYSET\_DRIVEN support bookmarks while cursor types SQL\_CURSOR\_DYNAMIC and SQL\_CURSOR\_FORWARD\_ONLY do not.

Before ODBC 3.0, a database could specify only whether it supported bookmarks or not: there was no interface to provide this information for each cursor type. There was no way for a database server to indicate for what kind of cursor bookmarks were supported. For ODBC 2 applications, the ODBC driver returns that it does support bookmarks. There is therefore nothing to prevent you from trying to use bookmarks with dynamic cursors; however, do not use this combination.

