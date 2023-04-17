<!-- loioa50e731a84f21015928ca9f6e50336cc -->

# Connection-Level Variables

Connection-level variables are declared by the user, and can be used in procedures or in batches of SQL statements to hold information.



Connection-level variables are declared with the `CREATE VARIABLE` statement. The `CREATE VARIABLE` statement can be used anywhere except inside compound statements. Connection-level variables can be passed as parameters to procedures.

The syntax for `CREATE VARIABLE` is:

```
CREATE VARIABLE variable-name data-type
```

When a variable is created, it is initially set to NULL. You can set the value of connection-level variables in the same way as local variables, using the `SET` statement or using a `SELECT` statement with an `INTO` clause.

Connection-level variables exist until the connection is terminated, or until you explicitly drop the variable using the `DROP VARIABLE` statement. The following statement drops the variable *<con\_var\>*:

```
DROP VARIABLE con_var
```



<a name="loioa50e731a84f21015928ca9f6e50336cc__iq_refbb_139"/>

## Example

The following batch of SQL statements illustrates the use of connection-level variables:

```
CREATE VARIABLE con_var INT;
SET con_var = 10;
MESSAGE 'con_var = ', con_var;
```

Running this batch from ISQL displays this message on the server window:

```
con_var = 10
```



<a name="loioa50e731a84f21015928ca9f6e50336cc__iq_refbb_140"/>

## Compatibility

SAP Adaptive Server Enterprise does not support connection-level variables.

