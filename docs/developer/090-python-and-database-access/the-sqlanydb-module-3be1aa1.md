<!-- loio3be1aa116c5f1014b4f5913b81421966 -->

# The sqlanydb Module

To use the sqlanydb module from a Python script, you must first load it by including an *import* statement at the top of the file.

```
import sqlanydb
```

The sqlanydb module is thread-safe when using Python with threads.

> ### Note:  
> The SQLA/IQ Python driver now supports Python 3.9. The prerequisites to use the SQLA/IQ Python driver are as follows:
> 
> -   A full installation of the IQ/SQLA client.
> 
> -   Keep the IQ/SQLA environment variables created by the installation program on Windows.
> 
> -   If you do not have either of the environment variables *<IQDIR17\>* or *<SQLANY17\>*, append the directory that contains the `dbcapi.dll` file to the environment variable *<PYTHONPATH\>*.
> 
> -   If you have a 64-bit Python executable, append the full path of the directory that contains the 64-bit `dbcapi.dll` file to *<PYTHONPATH\>*.

