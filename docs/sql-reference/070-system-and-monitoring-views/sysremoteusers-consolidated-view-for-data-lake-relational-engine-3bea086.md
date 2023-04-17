<!-- loio3bea086e6c5f1014bac2b2cc97449637 -->

# SYSREMOTEUSERS Consolidated View for Data Lake Relational Engine

Each row of the SYSREMOTEUSERS view describes a user ID with the REMOTE system privilege \(a subscriber\), together with the status of messages that were sent to and from that user.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



The tables and columns that make up this view are provided in the SQL statement below. To learn more about a particular table or column, use the links provided beneath the view definition.

```
ALTER VIEW "SYS"."SYSREMOTEUSERS" AS SELECT u.user_name, r.consolidate, t.type_name, r.address, r.frequency, r.send_time,  
(if r.frequency = 'A' then NULL   
else if r.frequency = 'P' then 
if r.time_sent IS NULL then CURRENT TIMESTAMP 
else (select min( minutes( dateadd(mi, PROPERTY('TimeZoneAdjustment'), a.time_sent),      
60*hour(a.send_time) + minute( seconds( a.send_time, 59 ) ) ) )      
FROM SYS.ISYSREMOTEUSER a WHERE a.frequency = 'P' AND a.send_time = r.send_time ) endif 
else if CURRENT DATE + r.send_time > coalesce( dateadd(mi, PROPERTY('TimeZoneAdjustment'), r.time_sent), CURRENT TIMESTAMP) 
then CURRENT DATE + r.send_time 
else CURRENT DATE + r.send_time + 1        
endif   endif  endif) as next_send, r.log_send ,  
dateadd(mi, PROPERTY('TimeZoneAdjustment'), r.time_sent) 
as time_sent , r.log_sent, r.confirm_sent, r.send_count, r.resend_count,  
dateadd(mi, PROPERTY('TimeZoneAdjustment'), r.time_received) as time_received , 
r.log_received, r.confirm_received, r.receive_count, r.rereceive_count ,  
TODATETIMEOFFSET( r.time_sent, 0 ) as time_sent_utc ,  
TODATETIMEOFFSET( r.time_received, 0 ) as time_received_utc  
FROM SYS.ISYSREMOTEUSER r JOIN SYS.ISYSUSER u ON ( u.user_id = r.user_id ) JOIN SYS.ISYSREMOTETYPE t ON ( t.type_id = r.type_id )
```

