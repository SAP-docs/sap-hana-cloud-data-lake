<!-- loioa50c437184f210158954f0c74f409ce3 -->

# TIMESTAMP Special Value in Data Lake Relational Engine

Returns when each row in the table was last modified.



<a name="loioa50c437184f210158954f0c74f409ce3__timestamp_datatype1"/>

## Data Type

TIMESTAMP



<a name="loioa50c437184f210158954f0c74f409ce3__timestamp_remarks1"/>

## Remarks

When a column is declared with DEFAULT TIMESTAMP, a default value is provided for insert and load operations. The value is updated with the current date and time whenever the row is updated.

On INSERT and LOAD, DEFAULT TIMESTAMP has the same effect as CURRENT TIMESTAMP. On UPDATE, if a column with a default value of TIMESTAMP isn’t explicitly modified, the value of the column is changed to the current date and time.

> ### Note:  
> Data lake Relational Engine doesn’t support DEFAULT values of UTC TIMESTAMP or CURRENT UTC TIMESTAMP. Data lake Relational Engine generates an error every time an attempt is made to insert or update the DEFAULT value of a column of type UTC TIMESTAMP or CURRENT UTC TIMESTAMP.



<a name="loioa50c437184f210158954f0c74f409ce3__timestamp_standards1"/>

## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 