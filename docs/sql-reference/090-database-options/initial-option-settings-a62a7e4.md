<!-- loioa62a7e4a84f2101590b5985c24412166 -->

# Initial Option Settings

You can use stored procedures to configure the initial database option settings of a user.

You can connect to data lake Relational Engine through the TDS \(tabular data stream\) protocol \(Open Client and jConnect for JDBC connections\) or through the data lake Relational Engine protocol \(ODBC, Embedded SQL\).

If users have both TDS and the data lake Relational Engine-specific protocol, you can configure their initial settings using stored procedures. As it is shipped, data lake Relational Engine uses this method to set Open Client connections and jConnect connections to reflect default SAP Adaptive Server Enterprise behavior.

The initial settings are controlled using the `LOGIN_PROCEDURE` option, which is called after all the checks have been performed to verify that the connection is valid. The `LOGIN_PROCEDURE` option names a stored procedure to run when users connect. The default setting is to use the `sp_login_environment` system stored procedure. You can specify a different stored procedure.

The `sp_login_environment` procedure checks to see if the connection is being made over TDS. If it is, it calls the `sp_tsql_environment` procedure, which sets several options to new default values for the current connection.

**Related Information**  


[LOGIN\_PROCEDURE Option for Data Lake Relational Engine](login-procedure-option-for-data-lake-relational-engine-a63d00e.md "Specifies a login procedure that sets connection compatibility options at start-up.")

