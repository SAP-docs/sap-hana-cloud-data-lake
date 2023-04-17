<!-- loio816310ef6ce21014843fd1f778e6b339 -->

# Considerations for the Windows DllMain Function

ODBC functions should not be called directly or indirectly from the DllMain function in a Windows Dynamic Link Library. The DllMain entry point function is intended to perform only simple initialization and termination tasks. Calling ODBC functions like SQLFreeHandle, SQLFreeConnect, and SQLFreeEnv can create deadlocks and circular dependencies.

The following code example illustrates a bad programming practice. When the Microsoft ODBC Driver Manager detects that the last access to the ODBC driver has completed, it will do a driver unload. When the ODBC driver shuts down, it stops any active threads. Thread termination results in a recursive thread detach call into DllMain. Since the call into DllMain is serialized, and a call is underway, the new thread detach call will never get started. The ODBC driver will wait forever for its threads to terminate and your application will hang.

```
BOOL APIENTRY DllMain( HMODULE hinstDLL,
    DWORD  fdwReason,
    LPVOID lpvReserved
    )
{
    HANDLE      *handles;
    switch( fdwReason ) {
.
.
.
    case DLL_THREAD_DETACH:
        /* do thread cleanup */
        handles = (HANDLE *) TlsGetValue( TlsIndex );
        if( handles != NULL )
        {
            SQLHENV     tls_henv;
            SQLHDBC     tls_hdbc;
            
            tls_henv = (SQLHENV) handles[0];
            tls_hdbc = (SQLHDBC) handles[1];
            if( tls_hdbc != NULL )
                SQLFreeHandle( SQL_HANDLE_DBC, tls_hdbc );
            if( tls_henv != NULL )
                SQLFreeHandle( SQL_HANDLE_ENV, tls_henv );     
            handles[0] = NULL;
            handles[1] = NULL;
        }
        break;
.
.
.
    }
    return TRUE;        /* indicate success */
}
```

