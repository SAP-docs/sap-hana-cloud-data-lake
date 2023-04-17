<!-- loioa874949c84f210158f26cfc56b077cde -->

# REVERT\_TO\_V15\_OPTIMIZER Option for Data Lake Relational Engine

Setting this option ON forces the query optimizer to mimic older versions of data lake Relational Engine behavior.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa874949c84f210158f26cfc56b077cde__iq_refso_324"/>

## Default

OFF

 



<a name="loioa874949c84f210158f26cfc56b077cde__iq_refso_326"/>

## Remarks

Data lake Relational Engine supports several new join and grouping algorithms that leverage Hash and Hash-Range partitioned tables, as well as a few other new algorithms. By default, all of these new algorithms are considered by the optimizer and will be selected where valid and appropriate.

