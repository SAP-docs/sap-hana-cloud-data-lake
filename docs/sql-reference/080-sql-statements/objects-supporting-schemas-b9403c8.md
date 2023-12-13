<!-- loiob9403c88a15146ff84a2f37266f75c69 -->

# Objects Supporting Schemas



Object types that have an owner and are considered unique using *<owner-name\>*.*<object-name\>* can exist as part of a schema. For example, tables can be referenced as *<owner-name\>*.*<table-name\>*. Two users can each have a table named foo – user1.foo and user2.foo. Therefore, a table can be part of a schema. On the other hand, although an event can be referenced as user1.foo, two users cannot have an event named foo, so events are not eligible to be part of a schema.




<table>
<tr>
<th valign="top">

Object Types Supporting Schema

</th>
<th valign="top">

Object Types Not Supporting Schema

</th>
</tr>
<tr>
<td valign="top">

-   EXISTING TABLE
-   FUNCTION
-   INDEX \(Table owner determines ownership\)
-   MATERIALIZED VIEW
-   PROCEDURE
-   TABLE
-   TEXT CONFIGURATION
-   TEXT INDEX \(Table owner determines ownership\)
-   View



</td>
<td valign="top">

-   CERTIFICATE
-   DATABASE VARIABLE
-   DBSPACE
-   DOMAIN
-   EVENT \(Name is not unique for different owners\)
-   EXTERNLOGIN
-   JWT PROVIDER
-   LDAP SERVER
-   LOGICAL SERVER
-   LOGIN POLICY
-   LS POLICY
-   MESSAGE
-   MUTEX
-   REMOTE SERVER
-   ROLE - No owner
-   SCHEMA \(Cannot have recursive schemas\)
-   SEMAPHORE
-   SEQUENCE
-   SERVICE
-   TEMPORARY TRACE EVENT
-   TRIGGER
-   USER
-   VARIABLE



</td>
</tr>
</table>

