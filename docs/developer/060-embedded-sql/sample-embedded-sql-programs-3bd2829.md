<!-- loio3bd282936c5f10149748ea85fc2bad82 -->

# Sample Embedded SQL Programs

Sample Embedded SQL programs are included with the software.

They are placed in the <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\C</code> directory.

-   The static cursor Embedded SQL example, `cur.sqc`, demonstrates the use of static SQL statements.

-   The dynamic cursor Embedded SQL example, `dcur.sqc`, demonstrates the use of dynamic SQL statements.


To reduce the amount of code that is duplicated by the sample programs, the mainlines and the data printing functions have been placed into a separate file. This is `mainch.c` for character mode systems and `mainwin.c` for windowing environments.

The sample programs each supply the following three routines, which are called from the mainlines:

WSQLEX\_Init
:   Connects to the database and opens the cursor.

WSQLEX\_Process\_Command
:   Processes commands from the user, manipulating the cursor as necessary.

WSQLEX\_Finish
:   Closes the cursor and disconnects from the database.

The function of the mainline is to:

1.  Call the WSQLEX\_Init routine.

2.  Loop, getting commands from the user and calling WSQL\_Process\_Command until the user quits.

3.  Call the WSQLEX\_Finish routine.


Connecting to the database is done with the Embedded SQL CONNECT statement supplying the appropriate user ID and password.

In addition to these samples, you may find other programs and source files included with the software that demonstrate features available for particular platforms.

