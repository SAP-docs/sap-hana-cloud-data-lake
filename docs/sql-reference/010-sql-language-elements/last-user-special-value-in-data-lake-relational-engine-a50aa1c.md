<!-- loioa50aa1c884f21015a227c19d3c0845ea -->

# LAST USER Special Value in Data Lake Relational Engine

Returns the name of the user who last modified the row.



<a name="loioa50aa1c884f21015a227c19d3c0845ea__last_user_datatype1"/>

## Data Type

STRING



<a name="loioa50aa1c884f21015a227c19d3c0845ea__last_user_remarks1"/>

## Remarks

On INSERT and LOAD, this constant has the same effect as CURRENT USER. On UPDATE, if a column with a default value of LAST USER is not explicitly modified, it is changed to the name of the current user.

When combined with the DEFAULT TIMESTAMP, a default value of LAST USER can be used to record \(in separate columns\) both the user and the date and time a row was last changed.

LAST USER can be used as a default value in columns with character data types.

**Related Information**  


[CURRENT USER Special Value in Data Lake Relational Engine](current-user-special-value-in-data-lake-relational-engine-a50a173.md "Returns a string that contains the user ID of the current connection.")

[CURRENT TIMESTAMP Special Value in Data Lake Relational Engine](current-timestamp-special-value-in-data-lake-relational-engine-a50992b.md "Combines CURRENT DATE and CURRENT TIME to form a TIMESTAMP value containing the year, month, day, hour, minute, second, and fraction of a second.")

[USER Special Value in Data Lake Relational Engine](user-special-value-in-data-lake-relational-engine-a50cc71.md "Returns a string that contains the user ID of the current connection.")

