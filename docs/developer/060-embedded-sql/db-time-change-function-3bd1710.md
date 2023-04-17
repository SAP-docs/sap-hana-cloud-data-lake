<!-- loio3bd171096c5f10148c6ea619d0b28118 -->

# db\_time\_change Function

Notify the server that the time has changed on the client.



```
unsigned int db_time_change(
SQLCA * <sqlca>);

```



## Parameters

sqlca
:   A pointer to a SQLCA structure.



## Returns

TRUE if successful; FALSE otherwise.



## Remarks

This function permits clients to notify the server that the time has changed on the client. This function recalculates the time zone adjustment and sends it to the server. On Windows platforms, applications must call this function when they receive the WM\_TIMECHANGE message. This will make sure that UTC timestamps are consistent over time changes, time zone changes, or daylight savings time changeovers.

