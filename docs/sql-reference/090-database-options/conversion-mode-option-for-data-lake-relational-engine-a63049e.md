<!-- loioa63049e384f2101598cfe678ff7c4663 -->

# CONVERSION\_MODE Option for Data Lake Relational Engine

Restricts implicit conversion between binary data types \(BINARY, VARBINARY, and LONG BINARY\) and other non-binary data types \(BIT, TINYINT, SMALLINT, INT, UNSIGNED INT, BIGINT, UNSIGNED BIGINT, CHAR, VARCHAR, and LONG VARCHAR\) on various operations. Also allows all explicit conversions to be permitted as implicit conversions on various operations.



<a name="loioa63049e384f2101598cfe678ff7c4663__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63049e384f2101598cfe678ff7c4663__iq_refso_415"/>

## Default

0



<a name="loioa63049e384f2101598cfe678ff7c4663__iq_refso_417"/>

## Remarks

The default CONVERSION\_MODE value of 0 maintains implicit conversion behavior.

For explicit conversion, use CAST or CONVERT in queries.

