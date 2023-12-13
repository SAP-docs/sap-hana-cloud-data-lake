<!-- loioa638b35784f21015bad8a47292e44a25 -->

# HTTP\_SESSION\_TIMEOUT Option for Data Lake Relational Engine

Specifies the amount of time, in minutes, that the client waits for an HTTP session to time out before giving up.



<a name="loioa638b35784f21015bad8a47292e44a25__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa638b35784f21015bad8a47292e44a25__iq_refso_597"/>

## Default

30



<a name="loioa638b35784f21015bad8a47292e44a25__iq_refso_599"/>

## Remarks

This option sets the session timeout control for Web service applications. A Web service application can change the timeout value from within any request that owns the HTTP session, but a change to the timeout value can impact subsequent queued requests if the HTTP session times out. The Web application must include logic to detect whether a client is attempting to access an HTTP session that no longer exists. This can be done by examining the value of the SessionCreateTime connection property to determine whether a timestamp is valid: if the HTTP request is not associated with the current HTTP session, the SessionCreateTime connection property contains an empty string.

