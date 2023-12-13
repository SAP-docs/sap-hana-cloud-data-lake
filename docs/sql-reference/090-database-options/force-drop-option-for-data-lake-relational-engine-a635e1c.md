<!-- loioa635e1c884f21015b2219c69c35a8ad8 -->

# FORCE\_DROP Option for Data Lake Relational Engine

Causes data lake Relational Engine to leak, rather than reclaim, database storagespace during a DROP command.



<a name="loioa635e1c884f21015b2219c69c35a8ad8__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa635e1c884f21015b2219c69c35a8ad8__iq_refso_529"/>

## Default

OFF



<a name="loioa635e1c884f21015b2219c69c35a8ad8__iq_refso_531"/>

## Remarks

When force dropping objects, you must ensure that only the DBA is connected to the database. The server must be restarted immediately after a force drop.

> ### Caution:  
> Do not attempt to force drop objects unless SAP Technical Support has instructed you to do so.

FORCE\_DROP procedures for system recovery and database repair are described in *SAP HANA Cloud, Data Lake Relational Engine Backup, Restore, and Data Recovery*.

