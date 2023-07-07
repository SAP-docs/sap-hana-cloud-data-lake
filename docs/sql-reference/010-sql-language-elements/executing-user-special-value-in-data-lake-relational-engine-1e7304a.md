<!-- loio1e7304a51fbc478d935a686c7b2fa497 -->

# EXECUTING USER Special Value in Data Lake Relational Engine

SQL special value that returns the current effective user.



<a name="loio1e7304a51fbc478d935a686c7b2fa497__executing_user_datatype1"/>

## Data Type

STRING



<a name="loio1e7304a51fbc478d935a686c7b2fa497__executing_user_remarks1"/>

## Remarks

Use EXECUTING USER, INVOKING USER, SESSION USER, and PROCEDURE OWNER to determine which users can execute, and are executing, procedures and user-defined functions. Depending on how many layers of nesting in a particular procedure call, and based on whether the previous and current procedure are SQL SECURITY DEFINER or SQL SECURITY INVOKER, the EXECUTING USER, and INVOKING USER can and do change.

EXECUTING\_USER is equivalent to EXECUTING USER.



<a name="loio1e7304a51fbc478d935a686c7b2fa497__executing_user_standards1"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>

