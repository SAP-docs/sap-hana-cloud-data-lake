<!-- loioa51388a384f21015b004c0ed59d3a679 -->

# VARCHAR Data and Trailing Blanks in Data Lake Relational Engine

For a column of data type VARCHAR, trailing blanks within the data being inserted are handled differently depending on whether or not the data is enclosed in quotes.



Data inserted using INSERT, UPDATE, or LOAD TABLE can be:

-   Enclosed in quotes
-   Not enclosed in quotes
-   Binary

For a column of data type VARCHAR, trailing blanks within the data being inserted are handled as follows:

-   For data enclosed in quotes, trailing blanks are never trimmed.
-   For data not enclosed in quotes:
    -   Trailing blanks always trimmed on insert and update.
    -   For a LOAD statement, you can use the STRIP RTRIM/OFF LOAD option to specify whether to have the trailing blanks trimmed. The STRIP RTRIM/OFF option applies only to variable-length nonbinary data. For example, assume the following schema:

        ```
        CREATE TABLE t( c1 VARCHAR(3) );
        LOAD TABLE t( c1 ',' ) ........ STRIP RTRIM    // trailing blanks trimmed
        
        LOAD TABLE t( c1 ',' ) ........ STRIP OFF      // trailing blanks not trimmed
        
        LOAD TABLE t( c1 ASCII(3) ) ... STRIP RTRIM    // trailing blanks not trimmed
        LOAD TABLE t( c1 ASCII(3) ) ... STRIP OFF      // trailing blanks trimmed
        
        LOAD TABLE t( c1 BINARY ) ..... STRIP RTRIM    // trailing blanks trimmed
        LOAD TABLE t( c1 BINARY ) ..... STRIP OFF      // trailing blanks trimmed
        ```

    -   For binary data, trailing blanks are always trimmed.


When you write your applications, do not depend on the existence of trailing blanks in VARCHAR columns.

