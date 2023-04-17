<!-- loio3bcbde926c5f1014a802e3b03215f7b8 -->

# login\_procedure Option

Specifies a stored procedure that is called when a user connects via a database login or web service.



## Allowed Values

String



## Default

sp\_login\_environment



<a name="loio3bcbde926c5f1014a802e3b03215f7b8__login-procedure-option-scope"/>

## Scope


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

PUBLIC role



</th>
<th valign="top">

For current user



</th>
<th valign="top">

For other users



</th>
</tr>
<tr>
<td valign="top">

Allowed to set permanently?



</td>
<td valign="top">

Yes, with SET ANY SECURITY OPTION



</td>
<td valign="top">

Yes, with SET ANY SECURITY OPTION



</td>
<td valign="top">

Yes, with SET ANY SECURITY OPTION



</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?



</td>
<td valign="top">

Yes, with SET ANY SECURITY OPTION



</td>
<td valign="top">

Yes \(current connection only\), with SET ANY SECURITY OPTION



</td>
<td valign="top">

No



</td>
</tr>
</table>



## Remarks

By default, the sp\_login\_environment stored procedure is called. The login procedure is called after all the checks have been performed to verify that the connection is valid. The procedure specified by the login\_procedure option is not executed for event connections, but it is executed for normal login and web service connections.

You can create a custom login procedure by creating a new stored procedure and setting login\_procedure to the owner and name of this new procedure.

This custom procedure should call the dbo.sp\_login\_environment stored procedure at some point during its execution since it detects when a TDS connection occurs and sets appropriate database options using the dbo.sp\_tsql\_environment stored procedure. Failure to do so can break TDS-based connections. It is not a good practice to revise either of the dbo.sp\_login\_environment or dbo.sp\_tsql\_environment stored procedures.

A password expired error message with SQLSTATE '08WA0' can be signaled by a user-defined login procedure to indicate to a user that their password has expired. Signaling the error allows applications to check for the error and process expired passwords. However, it is better to use a login policy to implement password expiry and not a login procedure that returns the expired password error message.

If you use the NewPassword=\* connection parameter, signaling this error is required for the client libraries to prompt for a new password. If the procedure signals SQLSTATE '28000' \(invalid user ID or password\) or SQLSTATE '08WA0' \(expired password\), or the procedure raises an error with RAISERROR, the login fails and an error is returned to the user. If you signal any other error or if another error occurs, then the user login is successful and a message is written to the database server message log.



The following example shows how you can limit the total number of database connections.

```
CREATE PROCEDURE DBA.login_check( )
   BEGIN
      DECLARE INVALID_LOGON EXCEPTION FOR SQLSTATE '28000';
      // Allow a maximum of 3 concurrent connections
      IF( DB_PROPERTY( 'ConnCount' ) > 3 ) THEN
          SIGNAL INVALID_LOGON;
      ELSE
          CALL dbo.sp_login_environment;
      END IF;
   END
go

GRANT EXECUTE ON DBA.login_check TO PUBLIC
go

SET OPTION PUBLIC.login_procedure='DBA.login_check'
go
```

The following example shows how you can block connection attempts if the number of failed connections for a user exceeds 3 within a 30 minute period. All blocked attempts during the block out period receive an invalid password error and are logged as failures. The log is kept long enough for a DBA to analyze it.

```
CREATE TABLE DBA.ConnectionFailure(
    pk INT PRIMARY KEY DEFAULT AUTOINCREMENT,
    user_name CHAR(128) NOT NULL,
    tm TIMESTAMP NOT NULL DEFAULT CURRENT TIMESTAMP
)
go 

CREATE INDEX ConnFailTime ON DBA.ConnectionFailure(
    user_name, tm )
go 

CREATE EVENT ConnFail TYPE ConnectFailed
HANDLER
BEGIN
    DECLARE usr CHAR(128);
    SET usr = event_parameter( 'User' );
    // Put a limit on the number of failures logged.
    IF (SELECT COUNT(*) FROM DBA.ConnectionFailure
        WHERE user_name = usr
        AND tm >= DATEADD( minute, -30, CURRENT TIMESTAMP )
        ) < 20 
    THEN
        INSERT INTO DBA.ConnectionFailure( user_name )
            VALUES( usr );
        COMMIT;
        // Delete failures older than 7 days.
        DELETE DBA.ConnectionFailure
        WHERE user_name = usr
        AND tm < DATEADD( day, -7, CURRENT TIMESTAMP );
        COMMIT;
    END IF;
END
go

CREATE PROCEDURE DBA.login_check( )
BEGIN
    DECLARE usr CHAR(128);
    DECLARE INVALID_LOGON EXCEPTION FOR SQLSTATE '28000';
    SET usr = CONNECTION_PROPERTY( 'Userid' );
    // Block connection attempts from this user
    // if 3 or more failed connection attempts have occurred
    // within the past 30 minutes.
    IF ( SELECT COUNT( * ) FROM DBA.ConnectionFailure
        WHERE user_name = usr
        AND tm >= DATEADD( minute, -30,
            CURRENT TIMESTAMP ) ) >= 3 THEN
        SIGNAL INVALID_LOGON;
    ELSE
        CALL dbo.sp_login_environment;
    END IF;
END
go

GRANT EXECUTE ON DBA.login_check TO PUBLIC
go

SET OPTION PUBLIC.login_procedure='DBA.login_check'
go
```

The following example shows how to signal an error indicating that the user's password has expired. However, it is better to use a login policy to implement password expiry notification.

```
CREATE PROCEDURE DBA.check_expired_login( )
BEGIN
  DECLARE PASSWORD_EXPIRED EXCEPTION FOR SQLSTATE '08WA0';

  IF( <condition-to-check-for-expired-password> ) THEN
      SIGNAL PASSWORD_EXPIRED;
  ELSE
      CALL dbo.sp_login_environment;
  END IF;
END;
```

