<!-- loioa644aafb84f21015ad5fdadb6a18cd53 -->

# NOTIFY\_MODULUS Option for Data Lake Relational Engine

Controls the default frequency of notify messages issued by certain commands.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa644aafb84f21015ad5fdadb6a18cd53__iq_refso_806"/>

## Default

0



<a name="loioa644aafb84f21015ad5fdadb6a18cd53__iq_refso_808"/>

## Remarks

This option sets the default number of notify messages data lake Relational Engine issued for certain commands that produce them. The NOTIFY clause for some of the commands \(such as CREATE INDEX, LOAD TABLE, and DELETE\) overrides this value. Other commands that do not support the NOTIFY clause always use this value. The default does not restrict the number of messages you can receive.

