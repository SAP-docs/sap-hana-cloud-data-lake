<!-- loioa631963f84f2101592f8f2ded17059a5 -->

# COOPERATIVE\_COMMIT\_TIMEOUT Option for Data Lake Relational Engine

Governs when a COMMIT entry in the transaction log is written to disk.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa631963f84f2101592f8f2ded17059a5__iq_refso_435"/>

## Default

250 milliseconds



<a name="loioa631963f84f2101592f8f2ded17059a5__iq_refso_437"/>

## Remarks

The database server waits for the specified number of milliseconds for other connections to fill a page of the log before writing to disk.

**Related Information**  


[COOPERATIVE\_COMMITS Option for Data Lake Relational Engine](cooperative-commits-option-for-data-lake-relational-engine-a631c5c.md "Controls when commits are written to disk.")

