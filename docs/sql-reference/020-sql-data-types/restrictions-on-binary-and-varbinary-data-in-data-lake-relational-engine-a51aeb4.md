<!-- loioa51aeb4a84f21015a0a4e94143cca9b7 -->

# Restrictions on BINARY and VARBINARY Data in Data Lake Relational Engine

Restrictions apply to columns containing BINARY and VARBINARY data.



-   You cannot use the aggregate functions SUM, AVG, STDDEV, or VARIANCE with the binary data types. The aggregate functions MIN, MAX, and COUNT do support the binary data types BINARY and VARBINARY.

-   HNG, WD, DATE, TIME, and DTTM indexes do not support BINARY or VARBINARY data.

-   Only the default index, CMP index, and TEXT index types are supported for BINARY and VARBINARY data greater than 255 bytes in length.

-   Bit operations are supported on BINARY and VARBINARY data that is 8 bytes or less in length.


