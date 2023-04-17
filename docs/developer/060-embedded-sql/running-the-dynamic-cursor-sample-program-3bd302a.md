<!-- loio3bd302a16c5f1014aee6c1e19bbdde96 -->

# Running the Dynamic Cursor Sample Program

Run the dynamic cursor sample program.



## Prerequisites

For Windows, a recent version of Microsoft Visual Studio is required.

For x86/x64 platform builds with Microsoft Visual Studio, you must set up the correct environment for compiling and linking. This is typically done using the Microsoft Visual Studio `vcvars32.bat` or `vcvars64.bat` \(called `vcvarsamd64.bat` in older versions of Microsoft Visual Studio\).



## Context

The executable files and corresponding source code are located in the <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\C</code> directory.



## Procedure

1.  Start the sample database, <code><i>iqdemo.db</i></code>.

2.  Files to build the sample programs are supplied with the sample code.

    For Windows, run the `build.bat` batch file.

    If you are getting build errors, try specifying the target platform \(`x86` or `x64`\) as an argument to `build.bat`. Here is an example.

    ```
    build x64
    ```

    For UNIX and Linux, use the shell script `build.sh` to build the example.

3.  For the 32-bit Windows example, run the file `dcurwin.exe`.

    For the 64-bit Windows example, run the file `dcurx64.exe`.

    You can call a function in an external library from a stored procedure or function. You can call functions in a DLL under Windows operating systems and in a shared object on UNIX and Linux.

    For the UNIX/Linux example, run the file `dcur`.

4.  Each sample program presents a console-type user interface and prompts you for a command. Enter the following connection string to connect to the sample database:

    ```
    DSN=SAP IQ 17 Demo;PWD=sql
    ```

5.  Each sample program prompts you for a table. Choose one of the tables in the sample database. For example, you can enter ***Customers*** or ***Employees***.

6.  Follow the on-screen instructions.




## Results

The various commands manipulate a database cursor and print the query results on the screen. Enter the letter of the command that you want to perform. Some systems may require you to press Enter after the letter.

