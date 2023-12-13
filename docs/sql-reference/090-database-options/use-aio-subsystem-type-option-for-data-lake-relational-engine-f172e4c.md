<!-- loiof172e4cc5f134c98ad2cfcb6ecda3b6c -->

# USE\_AIO\_SUBSYSTEM\_TYPE Option for Data Lake Relational Engine

Enables you to select the underlying subsystem for use with the asynchronous IO \(AIO\)-based implementation of the data lake Relational Engine prefetch manager.



<a name="loiof172e4cc5f134c98ad2cfcb6ecda3b6c__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loiof172e4cc5f134c98ad2cfcb6ecda3b6c__iq_refso_855"/>

## Default

0



<a name="loiof172e4cc5f134c98ad2cfcb6ecda3b6c__iq_refso_857"/>

## Remarks

When set to zero, if the cloud storage cannot be identified, then the value of 3 \(batched AIO requests\) is automatically used.


