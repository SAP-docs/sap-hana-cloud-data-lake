<!-- loio770c29dac247442cb39b2cbc89be1f48 -->

# PREFETCH\_HASH\_PERCENT Option for Data Lake Relational Engine

Specifies the percent of prefetch resources in queries involving hash-based algorithms.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loio770c29dac247442cb39b2cbc89be1f48__iq_refso_855"/>

## Default

20



<a name="loio770c29dac247442cb39b2cbc89be1f48__inb"/>

## Scope

Option can be set at the database \(PUBLIC\) or user level. At the database level, the value becomes the default for any new user, but has no impact on existing users. At the user level, overrides the PUBLIC value for that user only. No system privilege is required to set option for self. System privilege is required to set at database level or at user level for any user other than self.

Can be set temporary for an individual connection or for the PUBLIC role. Takes effect immediately.

