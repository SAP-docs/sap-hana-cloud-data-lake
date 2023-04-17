<!-- loio2c5e01a10afe4078965db40e57eac0b0 -->

# ENABLE\_AIO\_PERF\_TRACING Option for Data Lake Relational Engine

Enables performance tracing in the asynchronous IO \(AIO\)-based implementation of prefetch manager.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loio2c5e01a10afe4078965db40e57eac0b0__iq_refso_855"/>

## Default

OFF



<a name="loio2c5e01a10afe4078965db40e57eac0b0__iq_refso_857"/>

## Remarks

The following values are written to the `iqmsg` file at every 1-second interval:


<table>
<tr>
<th valign="top">

Value



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

AIO\_COUNT



</td>
<td valign="top">

Total number of AIO requests submitted



</td>
</tr>
<tr>
<td valign="top">

AIO\_SUBMISSION\_TIME\_PER\_AIO



</td>
<td valign="top">

Average AIO submission time



</td>
</tr>
<tr>
<td valign="top">

AIO\_INFRA\_TIME\_PER\_AIO



</td>
<td valign="top">

Average overhead added by the AIO layer before the AIO request is actually submitted to OS



</td>
</tr>
<tr>
<td valign="top">

AIO\_COMPLETION\_TIME\_PER\_AIO



</td>
<td valign="top">

Average time taken to complete each AIO



</td>
</tr>
<tr>
<td valign="top">

AIO\_TOTAL\_TIME\_PER\_AIO



</td>
<td valign="top">

Average time taken to complete each AIO, including the average time taken for the post-processing of read blocks.



</td>
</tr>
<tr>
<td valign="top">

AIO\_BATCH\_SUBMIT\_COUNT



</td>
<td valign="top">

Number of batched AIO requests submitted to OS.



</td>
</tr>
<tr>
<td valign="top">

AIO\_BATCH\_SUBMISSION\_TIME\_PER\_SUBMIT



</td>
<td valign="top">

Average time taken for the submission of batched AIO requests per submit.



</td>
</tr>
<tr>
<td valign="top">

AIO\_ASYNC\_SUBMISSION\_TIME\_PER\_SUBMIT



</td>
<td valign="top">

Average time taken for the submission of data lake Relational Engine-based AIO requests per submit.



</td>
</tr>
</table>

Sample of an AIO performance trace written to the `iqmsg` file:

```
I. 12/21 09:35:50. 0000000000 140338210182912 AIO_SYSTEM::STATS_MONITOR::   AIO_COUNT: 0
I. 12/21 09:35:50. 0000000000 140338210182912 AIO_SYSTEM::STATS_MONITOR::   AIO_SUBMISSION_TIME_PER_AIO: 0
I. 12/21 09:35:50. 0000000000 140338210182912 AIO_SYSTEM::STATS_MONITOR::   AIO_INFRA_TIME_PER_AIO: 0
I. 12/21 09:35:50. 0000000000 140338210182912 AIO_SYSTEM::STATS_MONITOR::   AIO_COMPLETION_TIME_PER_AIO: 0
I. 12/21 09:35:50. 0000000000 140338210182912 AIO_SYSTEM::STATS_MONITOR::   AIO_TOTAL_TIME_PER_AIO: 0
I. 12/21 09:35:50. 0000000000 140338210182912 AIO_SYSTEM::STATS_MONITOR::   AIO_BATCH_SUBMIT_COUNT: 0
I. 12/21 09:35:50. 0000000000 140338210182912 AIO_SYSTEM::STATS_MONITOR::  AIO_BATCH_SUBMISSION_TIME_PER_SUBMIT: 0
I. 12/21 09:35:50. 0000000000 140338210182912 AIO_SYSTEM::STATS_MONITOR::   AIO_ASYNC_SUBMISSION_TIME_PER_SUBMIT: 0

```

