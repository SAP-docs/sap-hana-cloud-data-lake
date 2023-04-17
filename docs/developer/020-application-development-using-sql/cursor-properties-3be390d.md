<!-- loio3be390d06c5f1014ab55fb417b72bf8d -->

# Cursor Properties

You request a cursor type, either explicitly or implicitly, from the programming interface. Different interface libraries offer different choices of cursor types.

For example, JDBC and ODBC specify different cursor types.

Each cursor type is defined by several characteristics:

Uniqueness
:   Declaring a cursor to be unique forces the query to return all the columns required to uniquely identify each row. Often this means returning all the columns in the primary key. Any columns required but not specified are added to the result set. The default cursor type is non-unique.

Updatability
:   A cursor declared as read-only cannot be used in a positioned update or delete operation. The default cursor type is updatable.

Scrollability
:   You can declare cursors to behave different ways as you move through the result set. Some cursors can fetch only the current row or the following row. Others can move backward and forward through the result set.

Sensitivity
:   Changes to the database may or may not be visible through a cursor.

These characteristics may have significant side effects on performance and on database server memory usage.

Cursors with a variety of mixes of these characteristics are possible. When you request a cursor of a given type, a match to those characteristics is attempted.

There are some occasions when not all characteristics can be supplied. For example, insensitive cursors must be read-only. If your application requests an updatable insensitive cursor, a different cursor type \(value-sensitive\) is supplied instead.

