<!-- loioa64833fa84f21015aaffdb1a825e33cd -->

# POST\_LOGIN\_PROCEDURE Option for Data Lake Relational Engine

Specifies a login procedure whose result set contains messages that are displayed by the client application immediately after a user successfully logs in.



<a name="loioa64833fa84f21015aaffdb1a825e33cd__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa64833fa84f21015aaffdb1a825e33cd__iq_refso_835"/>

## Default

dbo.sa\_post\_login\_procedure



<a name="loioa64833fa84f21015aaffdb1a825e33cd__iq_refso_837"/>

## Remarks

The default post login procedure, dbo.sa\_post\_login\_procedure, executes immediately after a user successfully logs in.

The post login procedure supports the client applications Interactive SQL, and Interactive SQL Classic.

**Related Information**  


[LOGIN\_PROCEDURE Option for Data Lake Relational Engine](login-procedure-option-for-data-lake-relational-engine-a63d00e.md "Specifies a login procedure that sets connection compatibility options at start-up.")

