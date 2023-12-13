<!-- loioa63b24dd84f21015bdd0c32fe987946f -->

# JAVA\_VM\_OPTIONS Option for Data Lake Relational Engine

Specifies command line options that the database server uses when it launches the Java VM.



<a name="loioa63b24dd84f21015bdd0c32fe987946f__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63b24dd84f21015bdd0c32fe987946f__iq_refso_655"/>

## Default

Empty string



<a name="loioa63b24dd84f21015bdd0c32fe987946f__iq_refso_657"/>

## Remarks

JAVA\_VM\_OPTIONS specifies options that the database server uses when launching the Java VM specified by the JAVA\_LOCATION option. These additional options can be used to set up the Java VM for debugging purposes or to run as a service on UNIX platforms. In some cases, additional options are required to use the Java VM in 64-bit mode instead of 32-bit mode.

**Related Information**  


[JAVA\_LOCATION Option for Data Lake Relational Engine](java-location-option-for-data-lake-relational-engine-a63af5b.md "Specifies the path of the Java VM for the database.")

