<!-- loioa63e2b9784f21015983992c1d7a76694 -->

# MAX\_CURSOR\_COUNT Option for Data Lake Relational Engine

Specifies a resource governor to limit the maximum number of cursors that a connection can use at once.



<a name="loioa63e2b9784f21015983992c1d7a76694__section_uks_z43_ywb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63e2b9784f21015983992c1d7a76694__iq_refso_728"/>

## Default

50



<a name="loioa63e2b9784f21015983992c1d7a76694__iq_refso_730"/>

## Remarks

This option limits the number of cursors per connection that a user can have. If an operation exceeds the limit for a connection, an error is generated indicating that the limit has been exceeded.

If a connection executes a stored procedure, the procedure is executed under the permissions of the procedure owner. However, the resources used by the procedure are assigned to the current connection.

