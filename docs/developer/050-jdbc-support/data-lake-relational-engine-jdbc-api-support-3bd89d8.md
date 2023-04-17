<!-- loio3bd89d896c5f10149ec2e318c4aba994 -->

# Data Lake Relational Engine JDBC API Support

Some optional methods of the java.sql.Blob interface are not supported by the data lake Relational Engine JDBC driver.



These optional methods are:

-   long position\( Blob pattern, long start \);
-   long position\( byte\[\] pattern, long start \);
-   OutputStream setBinaryStream\( long pos \)
-   int setBytes\( long pos, byte\[\] bytes \)
-   int setBytes\( long pos, byte\[\] bytes, int offset, int len \);
-   void truncate\( long len \);

