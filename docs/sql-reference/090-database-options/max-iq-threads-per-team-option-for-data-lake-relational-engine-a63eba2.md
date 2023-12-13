<!-- loioa63eba2484f21015b317cbd7314206f7 -->

# MAX\_IQ\_THREADS\_PER\_TEAM Option for Data Lake Relational Engine

Controls the number of threads allocated to perform a single operation \(such as a LIKE predicate on a column\) executing within a connection.



<a name="loioa63eba2484f21015b317cbd7314206f7__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63eba2484f21015b317cbd7314206f7__iq_refso_742"/>

## Default

144



<a name="loioa63eba2484f21015b317cbd7314206f7__iq_refso_744"/>

## Remarks

Allows you to constrain the number of threads \(and thereby the amount of system resources\) allocated to a single operation. The total for all simultaneously executing teams for this connection is limited by the related option, MAX\_IQ\_THREADS\_PER\_CONNECTION.

**Related Information**  


[MAX\_IQ\_THREADS\_PER\_CONNECTION Option for Data Lake Relational Engine](max-iq-threads-per-connection-option-for-data-lake-relational-engine-a63e8bf.md "Controls the number of threads for each connection.")

