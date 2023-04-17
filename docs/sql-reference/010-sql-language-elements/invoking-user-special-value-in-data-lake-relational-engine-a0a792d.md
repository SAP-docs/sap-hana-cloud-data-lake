<!-- loioa0a792d163fa45d09fbbf2e08536eb76 -->

# INVOKING USER Special Value in Data Lake Relational Engine

Returns the user that invoked the current procedure, or returns the current logged in user if no procedure is executing.



<a name="loioa0a792d163fa45d09fbbf2e08536eb76__invoking_user_dataypte1"/>

## Data Type

STRING



<a name="loioa0a792d163fa45d09fbbf2e08536eb76__invoking_user_remarks1"/>

## Remarks

Use INVOKING USER, SESSION USER, EXECUTING USER, and PROCEDURE OWNER to determine which users can execute, and are executing, procedures. Depending on how many layers of nesting in a particular procedure call, the INVOKING USER and EXECUTING USER can and do change.

INVOKING\_USER is equivalent to INVOKING USER.



<a name="loioa0a792d163fa45d09fbbf2e08536eb76__invoking_user_standards1"/>

## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 