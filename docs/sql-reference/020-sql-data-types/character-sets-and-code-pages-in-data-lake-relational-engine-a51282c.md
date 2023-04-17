<!-- loioa51282c684f21015b7f488516b09d8b0 -->

# Character Sets and Code Pages in Data Lake Relational Engine

Character data is placed in the database using the exact binary representation that is passed from the application.



This placement usually means that character data is stored in the database with the binary representation of the character set used by your system. You can find documentation about character sets in the documentation for your operating system.

This problem also appears if you have two clients using the same multiuser server, but running with different code pages. Data inserted or updated by one client might appear incorrect to another.

If any of your applications use the extended characters in the upper half of the code page, make sure that all clients and all machines using the database use the same or a compatible code page.

