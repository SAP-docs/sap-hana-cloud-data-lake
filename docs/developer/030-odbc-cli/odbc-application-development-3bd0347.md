<!-- loio3bd0347e6c5f1014ab07af754440aebe -->

# ODBC Application Development

Every C/C++ source file that calls ODBC functions must include a platform-specific ODBC header file. Each platform-specific header file includes the main ODBC header file `odbc.h`, which defines all the functions, data types, and constant definitions required to write an ODBC program.

Perform the following tasks to include the ODBC header file in a C/C++ source file:

1.  Add an include line referencing the appropriate platform-specific header file to your source file. The lines to use are as follows:


    <table>
    <tr>
    <th valign="top">

    Operating System


    
    </th>
    <th valign="top">

    Include Line


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    Windows


    
    </td>
    <td valign="top">

    \#include "ntodbc.h"


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Linux


    
    </td>
    <td valign="top">

    \#include "unixodbc.h"


    
    </td>
    </tr>
    </table>
    
2.  Add the directory containing the header file to the include path for your compiler.

    Both the platform-specific header files and `odbc.h` are installed in the `SDK\include` subdirectory of the database server software directory.

3.  When building ODBC applications for Linux, you might have to define the macro "UNIX" for 32-bit applications or "UNIX64" for 64-bit applications to obtain the correct data alignment and sizes. This step is not required if you are using one of the following supported compilers:

    -   GNU C/C++ compiler on any supported platform


Once your source code has been written, you are ready to compile and link the application.

