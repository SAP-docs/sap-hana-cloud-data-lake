<!-- loioa631c5ca84f21015802ac2f810821acb -->

# COOPERATIVE\_COMMITS Option for Data Lake Relational Engine

Controls when commits are written to disk.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa631c5ca84f21015802ac2f810821acb__iq_refso_439"/>

## Default

ON



<a name="loioa631c5ca84f21015802ac2f810821acb__iq_refso_441"/>

## Remarks

If CREATE\_HG\_AND\_FORCE\_PHYSICAL\_DELETE is set to ON, the default, the database server does not immediately write the COMMIT to the disk. Instead, it requires the application to wait for a maximum length set by the COOPERATIVE\_COMMIT\_TIMEOUT option for something else to put on the pages before the commit is written to disk.

**Related Information**  


[COOPERATIVE\_COMMIT\_TIMEOUT Option for Data Lake Relational Engine](cooperative-commit-timeout-option-for-data-lake-relational-engine-a631963.md "Governs when a COMMIT entry in the transaction log is written to disk.")

