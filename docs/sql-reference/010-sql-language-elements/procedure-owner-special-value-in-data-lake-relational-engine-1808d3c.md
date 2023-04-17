<!-- loio1808d3c94e5941c390edd31ef7e6c463 -->

# PROCEDURE OWNER Special Value in Data Lake Relational Engine

Returns the owner of the current procedure, or NULL if queried outside of a procedure context.



<a name="loio1808d3c94e5941c390edd31ef7e6c463__procedure_owner_datatype1"/>

## Data Type

STRING



<a name="loio1808d3c94e5941c390edd31ef7e6c463__procedure_owner_remarks1"/>

## Remarks

Use PROCEDURE OWNER, INVOKING USER, SESSION USER, and EXECUTING USER to determine which users can execute, and are executing, procedures and user-defined functions. Depending on how many layers of nesting in a particular procedure call, the EXECUTING USER and INVOKING USER can and do change.

PROCEDURE\_OWNER is equivalent to PROCEDURE OWNER.



<a name="loio1808d3c94e5941c390edd31ef7e6c463__procedure_owner_standards1"/>

## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 