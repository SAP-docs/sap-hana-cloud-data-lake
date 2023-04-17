<!-- loioa629c37084f21015af809841ea9776c4 -->

# Scope and Duration of Database Options

You can set options at three levels of scope: public, user, and temporary.

Temporary options take precedence over user and public settings. User-level options take precedence over public settings. If you set a user-level option for the current user, the corresponding temporary option is set as well.

Some options, such as `COMMIT_THREADS_PERCENT` behavior, are database-wide in scope. Setting these options requires specific permissions. Other options, such as `ISOLATION_LEVEL`, can also be applied to only the current connection, and need no special permissions.

Changes to option settings take place at different times, depending on the option. Changing a global option such as `RECOVERY_TIME` takes place the next time the server is started. Some of the options that take effect after the server is restarted:

-   `CACHE_PARTITIONS`
-   `CHECKPOINT_TIME`
-   `PREFETCH_BUFFER_LIMIT`
-   `PREFETCH_BUFFER_PERCENT`
-   `RECOVERY_TIME`
-   `SWEEPER_THREADS_PERCENT`
-   `WASH_AREA_BUFFERS_PERCENT`

Options that affect only the current connection generally take place immediately. For example, you can change option settings in the middle of a transaction.

> ### Caution:  
> Changing options when a cursor is open can lead to unreliable results. For example, changing `DATE_FORMAT` might not change the format for the next row when a cursor is opened. Depending on the way the cursor is being retrieved, it might take several rows before the change works its way to the user.

