<!-- loio09575186684644a495e5991afb46d19c -->

# SESSION USER Special Value in Data Lake Relational Engine

SQL special value that stores the user that is currently logged in.



<a name="loio09575186684644a495e5991afb46d19c__session_user_datatype1"/>

## Data Type

STRING



<a name="loio09575186684644a495e5991afb46d19c__session_user_remarks1"/>

## Remarks

Use SESSION USER, INVOKING USER, EXECUTING USER, and PROCEDURE OWNER to determine which users can execute, and are executing, procedures and user-defined functions. Depending on how many layers of nesting in a particular procedure call, and based on whether the previous and current procedure are SQL SECURITY DEFINER or SQL SECURITY INVOKER, the INVOKING USER, and EXECUTING USER can and do change. However, SESSION USER always remains the logged in user.

SESSION\_USER is equivalent to SESSION USER.



<a name="loio09575186684644a495e5991afb46d19c__session_user_standards1"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>

