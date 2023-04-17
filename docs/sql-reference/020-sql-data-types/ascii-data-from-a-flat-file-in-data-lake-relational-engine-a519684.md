<!-- loioa519684a84f210159d3ca5bd67eeac55 -->

# ASCII Data from a Flat File in Data Lake Relational Engine

Any ASCII data loaded from a flat file into a binary type column \(BINARY or VARBINARY\) is stored as nibbles.



For example, if 0x1234 or 1234 is read from a flat file into a binary column, data lake Relational Engine stores the value as hexadecimal 1234. Data lake Relational Engine ignores the "0x" prefix. The data is rejected if the input data contains any characters out of the range 0 – 9, a – f, and A – F.

