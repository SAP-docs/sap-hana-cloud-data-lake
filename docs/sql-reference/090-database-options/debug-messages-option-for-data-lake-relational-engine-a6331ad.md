<!-- loioa6331adb84f21015ad4ae4e3d890bb7e -->

# DEBUG\_MESSAGES Option for Data Lake Relational Engine

Controls whether or not MESSAGE statements that include a DEBUG ONLY clause are executed.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa6331adb84f21015ad4ae4e3d890bb7e__iq_refso_469"/>

## Default

OFF



<a name="loioa6331adb84f21015ad4ae4e3d890bb7e__iq_refso_470"/>

## Remarks

This option controls the behavior of debugging messages in stored procedures that contain a MESSAGE statement with the DEBUG ONLY clause specified. By default, this option is set to OFF and debugging messages do not appear when the MESSAGE statement is executed.

DEBUG ONLY messages are inexpensive when the DEBUG\_MESSAGES option is set to OFF, so these statements can usually be left in stored procedures on a production system. However, they should be used sparingly in locations where they would be executed frequently; otherwise, they might result in a small performance penalty.

