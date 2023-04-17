<!-- loioa5999f2684f21015af3ca1367a1f9ef6 -->

# Understanding Statistics Reported by Stored Procedures

Many stored procedures report information on the state of data lake Relational Engine at the time the procedure executes.

This means that you get a snapshot view. For example, a report column that lists space in use by a connection shows only the space in use at the instant the procedure executes, not the maximum space used by that connection.

To monitor data lake Relational Engine usage over an extended period, use the data lake Relational Engine monitor, which collects and reports statistics from the time you start the monitor until you stop it, at an interval you specify.

