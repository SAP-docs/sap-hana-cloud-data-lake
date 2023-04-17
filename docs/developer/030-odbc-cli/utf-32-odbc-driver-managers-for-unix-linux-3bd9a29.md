<!-- loio3bd9a29c6c5f1014b3e2f7312a57028f -->

# UTF-32 ODBC Driver Managers for UNIX/Linux

Versions of ODBC driver managers that define SQLWCHAR as 32-bit \(UTF-32\) quantities cannot be used with the ODBC driver that supports wide calls since this driver is built for 16-bit SQLWCHAR.

For these cases, an ANSI-only version of the ODBC driver is provided. This version of the ODBC driver does not support the wide call interface \(for example, SQLConnectW\).

The shared object name of the driver is <code>libdbodbcansi<i>17</i>_r</code>. Only a threaded variant of the driver is provided.

The regular ODBC driver treats SQLWCHAR strings as UTF-16 strings. This driver cannot be used with some ODBC driver managers, such as iODBC, which treat SQLWCHAR strings as UTF-32 strings. When dealing with Unicode-enabled drivers, these driver managers translate narrow calls from the application to wide calls into the driver. An ANSI-only driver gets around this behavior, allowing the driver to be used with such driver managers, as long as the application does not make any wide calls. Wide calls through iODBC, or any other driver manager with similar semantics, remain unsupported.

