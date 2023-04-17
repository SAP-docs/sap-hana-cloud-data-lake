<!-- loio815e71c46ce210149f1b81ba006abedd -->

# The ODBC Driver Manager for UNIX/Linux

An ODBC driver manager for UNIX and Linux is included with the database server software.

The <code>libdbodm<i>17</i></code> shared object can be used on all supported UNIX and Linux platforms as an ODBC driver manager. The driver manager can be used to load any version 3.0 or later ODBC driver. The driver manager will not perform mappings between ODBC 1.0/2.0 calls and ODBC 3.x calls; therefore, applications using the driver manager must restrict their use of the ODBC feature set to version 3.0 and later. Also, the driver manager can be used by both threaded and non-threaded applications.

The driver manager can perform tracing of ODBC calls for any given connection. To turn on tracing, use the TraceLevel and TraceLog directives. These directives can be part of a connection string \(in the case where SQLDriverConnect is being used\) or within a DSN entry. The TraceLog directive identifies the tracing log file to contain the trace output for the connection. The TraceLevel directive governs the amount of tracing information wanted. The trace levels are:

NONE
:   No tracing information is printed.

MINIMAL
:   Routine name and parameters are included in the output.

LOW
:   In addition to the above, return values are included in the output.

MEDIUM
:   In addition to the above, the date and time of execution are included in the output.

HIGH
:   In addition to the above, parameter types are included in the output.

Third-party ODBC driver managers for UNIX and Linux are available also. Consult the documentation that accompanies these driver managers for information about their use.

