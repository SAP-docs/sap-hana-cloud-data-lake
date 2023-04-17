<!-- loio69afcb1ae3174ef9adb7d43c3341316a -->

# ASCII Data from a Flat File in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Any ASCII data loaded from a flat file into a binary type column \(BINARY or VARBINARY\) is stored as nibbles.



For example, if 0x1234 or 1234 is read from a flat file into a binary column, data lake Relational Engine stores the value as hexadecimal 1234. Data lake Relational Engine ignores the "0x" prefix. The data is rejected if the input data contains any characters out of the range 0 – 9, a – f, and A – F.

