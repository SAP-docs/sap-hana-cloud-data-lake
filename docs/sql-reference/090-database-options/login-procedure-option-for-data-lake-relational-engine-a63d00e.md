<!-- loioa63d00eb84f21015a4a5a5d4825b9fe7 -->

# LOGIN\_PROCEDURE Option for Data Lake Relational Engine

Specifies a login procedure that sets connection compatibility options at start-up.



<a name="loioa63d00eb84f21015a4a5a5d4825b9fe7__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63d00eb84f21015a4a5a5d4825b9fe7__iq_refso_703"/>

## Default

sp\_login\_environment system procedure



<a name="loioa63d00eb84f21015a4a5a5d4825b9fe7__iq_refso_705"/>

## Remarks

The sp\_login\_environment procedure checks to see if the connection is being made over TDS. If the connection is made over TDS, sp\_login\_environment calls the sp\_tsql\_environment procedure, which sets several options to new default values for the current connection.

**Related Information**  


[NON\_ANSI\_NULL\_VARCHAR Option for Data Lake Relational Engine](non-ansi-null-varchar-option-for-data-lake-relational-engine-a643a35.md "Controls whether zero-length VARCHAR data is treated as NULLs for insert, load, and update operations.")

[Initial Option Settings](initial-option-settings-a62a7e4.md "You can use stored procedures to configure the initial database option settings of a user.")

