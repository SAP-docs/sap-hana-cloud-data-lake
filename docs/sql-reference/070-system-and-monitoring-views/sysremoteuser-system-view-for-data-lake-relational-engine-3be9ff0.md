<!-- loio3be9ff0f6c5f1014937ee9f5500be619 -->

# SYSREMOTEUSER System View for Data Lake Relational Engine

Each row in the SYSREMOTEUSER system view describes a user ID with the REMOTE system privilege \(a subscriber\), together with the status of messages that were sent to and from that user. The underlying system table for this view is ISYSREMOTEUSER.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<table>
<tr>
<th valign="top">

Column name



</th>
<th valign="top">

Data type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

user\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The user number of the user with REMOTE privilege.



</td>
</tr>
<tr>
<td valign="top">

consolidate



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

Indicates whether the user was granted CONSOLIDATE privilege \(Y\) or REMOTE privileges \(N\).



</td>
</tr>
<tr>
<td valign="top">

type\_id



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Identifies which of the message systems is used to send messages to the user.



</td>
</tr>
<tr>
<td valign="top">

address



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The address to which messages are to be sent. The address must be appropriate for the address\_type.



</td>
</tr>
<tr>
<td valign="top">

frequency



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

How frequently messages are sent.



</td>
</tr>
<tr>
<td valign="top">

send\_time



</td>
<td valign="top">

TIME



</td>
<td valign="top">

The next time messages are to be sent to this user.



</td>
</tr>
<tr>
<td valign="top">

log\_send



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Messages are sent only to subscribers for whom log\_send is greater than log\_sent.



</td>
</tr>
<tr>
<td valign="top">

time\_sent



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

The local time the most recent message was sent to this subscriber.



</td>
</tr>
<tr>
<td valign="top">

log\_sent



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The log offset for the most recently sent operation.



</td>
</tr>
<tr>
<td valign="top">

confirm\_sent



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The log offset for the most recently confirmed operation from this subscriber.



</td>
</tr>
<tr>
<td valign="top">

send\_count



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

How many messages have been sent.



</td>
</tr>
<tr>
<td valign="top">

resend\_count



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Counter to ensure that messages are applied only once at the subscriber database.



</td>
</tr>
<tr>
<td valign="top">

time\_received



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

The local time when the most recent message was received from this subscriber.



</td>
</tr>
<tr>
<td valign="top">

log\_received



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The log offset in the database of the subscriber for the operation that was most recently received at the current database.



</td>
</tr>
<tr>
<td valign="top">

confirm\_received



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The log offset in the database of the subscriber for the most recent operation for which a confirmation message has been sent.



</td>
</tr>
<tr>
<td valign="top">

receive\_count



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

How many messages have been received.



</td>
</tr>
<tr>
<td valign="top">

rereceive\_count



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Counter to ensure that messages are applied only once at the current database.



</td>
</tr>
<tr>
<td valign="top">

time\_sent\_utc



</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE



</td>
<td valign="top">

The UTC time the most recent message was sent to this subscriber.



</td>
</tr>
<tr>
<td valign="top">

time\_received\_utc



</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE



</td>
<td valign="top">

The UTC time when the most recent message was received from this subscriber.



</td>
</tr>
</table>

