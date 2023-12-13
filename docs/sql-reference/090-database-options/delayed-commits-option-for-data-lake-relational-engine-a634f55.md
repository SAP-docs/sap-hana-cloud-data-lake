<!-- loioa634f55784f21015aa139fb52558ad7a -->

# DELAYED\_COMMITS Option for Data Lake Relational Engine

Determines when the server returns control to an application following a COMMIT.



<a name="loioa634f55784f21015aa139fb52558ad7a__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa634f55784f21015aa139fb52558ad7a__iq_refso_510"/>

## Default

OFF. This corresponds to ISO COMMIT behavior.



<a name="loioa634f55784f21015aa139fb52558ad7a__iq_refso_511"/>

## Remarks

When set to OFF, the application must wait until the COMMIT is written to disk. This option must be set to OFF for ANSI/ISO COMMIT behavior.

