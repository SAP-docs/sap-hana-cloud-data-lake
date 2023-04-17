<!-- loioa629f1ee84f2101590a3eb5cda52a489 -->

# Temporary Options

Adding the TEMPORARY keyword to the SET OPTION statement changes the duration of the change.

Ordinarily an option change is permanent: it will not change until it is explicitly changed using the SET OPTION statement.

When the SET TEMPORARY OPTION statement is executed, the new option value takes effect only for the current connection, and only for the duration of the connection.

When the SET TEMPORARY OPTION is used to set a PUBLIC option, the change is in place for as long as the database is running. When the database is shut down, TEMPORARY options for the PUBLIC user ID revert back to their permanent value.

Setting an option for the PUBLIC user ID temporarily offers a security advantage. For example, when the LOGIN\_MODE option is enabled, the database relies on the login security of the system on which it is running. Enabling LOGIN\_MODE temporarily means that a database relying on the security of a Windows domain will not be compromised if the database is shut down and copied to a local machine. In this case, the LOGIN\_MODE option reverts to its permanent value, which could be Standard, a mode where integrated logins are not permitted.

