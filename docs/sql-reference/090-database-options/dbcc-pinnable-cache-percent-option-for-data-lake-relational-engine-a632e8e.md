<!-- loioa632e8ee84f210158a4486c892490f49 -->

# DBCC\_PINNABLE\_CACHE\_PERCENT Option for Data Lake Relational Engine

Controls the percent of the cache used by the sp\_iqcheckdb system stored procedure.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa632e8ee84f210158a4486c892490f49__iq_refso_465"/>

## Default

50



<a name="loioa632e8ee84f210158a4486c892490f49__iq_refso_467"/>

## Remarks

The sp\_iqcheckdb system stored procedure works with a fixed number of buffers, as determined by this option. By default, a large percentage of the cache is reserved to maximize sp\_iqcheckdb performance.

