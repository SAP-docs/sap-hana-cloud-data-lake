<!-- loioa655979284f21015921582161fa7303b -->

# SORT\_PINNABLE\_CACHE\_PERCENT Option for Data Lake Relational Engine

Specifies the maximum percentage of currently available buffers a sort object tries to pin.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa655979284f21015921582161fa7303b__iq_refso_943"/>

## Default

20



<a name="loioa655979284f21015921582161fa7303b__iq_refso_945"/>

## Remarks

For very large sorts, a larger value might help reduce the number of merge phases required by the sort. A larger number, however, might impact the sorts and hashes of other users running on the system. If you change this option, experiment to find the best value to increase performance, as choosing the wrong value might decrease performance.

