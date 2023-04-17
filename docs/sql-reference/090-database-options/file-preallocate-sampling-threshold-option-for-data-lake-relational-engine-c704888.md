<!-- loioc704888fb2bf47e99908498ed1d9f042 -->

# FILE\_PREALLOCATE\_SAMPLING\_THRESHOLD Option for Data Lake Relational Engine

Speeds up dbfile creation time if the underlying cloud storage is slow.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioc704888fb2bf47e99908498ed1d9f042__section_w4t_f2c_mz"/>

## Default

10 milliseconds



<a name="loioc704888fb2bf47e99908498ed1d9f042__section_yz5_32c_mz"/>

## Remarks

If you suspect a slow cloud storage, check the `.iqmsg` file for messages like these:

```
I. 03/30 11:31:05. 0000013261 139619391600384 Info: posix_fallocate fd=627 sample time 0.220000 sec.
I. 03/30 11:31:05. 0000013261 139619391600384 Info: posix_fallocate fd=627 second sample time 0.000000 sec.
I. 03/30 11:31:05. 0000013261 139619391600384 Info: posix_fallocate fd=627 sample time 0.000000 sec.
I. 03/30 11:31:05. 0000013261 139619391600384 Info: using posix_fallocate fd=627.  Sampling threshold was 0.050000 sec.

```

Convert the current value of FILE\_PREALLOCATE\_SAMPLING\_THRESHOLD to seconds and compare it to the values of sample time and second sample time. If the lower of sample time and second sample time exceeds the value of FILE\_PREALLOCATE\_SAMPLING\_THRESHOLD, set FILE\_PREALLOCATE\_SAMPLING\_THRESHOLD to a value greater than the smaller of the sample time and second sample time values.

