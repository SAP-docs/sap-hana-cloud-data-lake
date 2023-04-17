<!-- loio418e39de3c0f4540aef5839871b4d08c -->

# CSCONVERT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Converts strings between character sets.



```
CSCONVERT( 
<string-expression> ,
<target-charset-string> 
[ , <source-charset-string> [ , <options> ] ] 
)
```



## Parameters

 *<string-expression\>*
 :   The string to be converted.

  *<target-charset-string\>*
 :   The destination character set. *<target-charset-string\>* can be any of the supported character set labels. It can also be:

     db\_charset
     :   Equivalent to char\_charset. Specify this to use the CHAR character set used by the database.

      os\_charset
     :   Specify this to use the character set used by the operating system that is hosting the database server.

      char\_charset
     :   Equivalent to db\_charset. Specify this to use the CHAR character set used by the database.

      nchar\_charset
     :   Specify this to use the NCHAR character set used by the database.

   *<source-charset-string\>*
 :   The character set used for *<string-expression\>*. The default is db\_charset \(the database character set\). *<source-charset-string\>* can be any of the supported character set labels. It can also be:

     db\_charset
     :   Equivalent to char\_charset. Specify this to use the CHAR character set used by the database.

      os\_charset
     :   Specify this to use the character set used by the operating system that is hosting the database server.

      char\_charset
     :   Equivalent to db\_charset. Specify this to use the CHAR character set used by the database.

      nchar\_charset
     :   Specify this to use the NCHAR character set used by the database.

   options
 :   You can specify either or both of the following options:

     Read or write a byte order mark \(BOM\)
     :   Specify ***read\_bom=on*** or ***read\_bom=off*** to turn on or off reading byte order marks. Specify ***write\_bom=on*** or ***write\_bom=off*** to turn on or off writing byte order marks. By default, the behavior is read\_bom=on and write\_bom=off.

  

## Returns

LONG BINARY



## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard. In the ANSI/ISO SQL Standard, conversion of string data from one charset to another is accomplished with the CONVERT function \(not to be confused with the CONVERT function provided in the software\) which has different arguments than CSCONVERT.

 

## 1

This fragment treats the mytext column as if it were encoded in 'cp950' and converts it to 'cp936':

```
SELECT CSCONVERT( mytext, 'cp936', 'cp950' )
FROM mytable;
```

> ### Note:  
> Note that mytext may or may not actually be encoded in cp950 \(that may depend on the CHAR collation and/or the datatype of the mytext column\).



## 2

This fragment converts the mytext column from the database character set to the Simplified Chinese character set:

```
SELECT CSCONVERT( mytext, 'cp936' )
FROM mytable;
```

When the database server needs to access a local file such as the HDL diagnostics files, the server will implicitly convert the filename to the operating system character set before accessing the file.



## 3

This fragment converts the value in the filename column from the database character set to the operating system character set:

```
SELECT CSCONVERT( filename, 'os_charset' )
FROM mytable;
```



## 4

A table contains a list of file names. An external stored procedure takes a file name from this table as a parameter and reads information directly out of that file. The following statement works when character set conversion is not required:

```
SELECT MYFUNC( filename )
FROM mytable;
```

The *<mytable\>* clause indicates a table with a filename column. However, if you need to convert the file name to the character set of the operating system, you would use the following statement:

```
SELECT MYFUNC( csconvert( filename, 'os_charset' ) )
FROM mytable;
```

**Related Information**  


[CSCONVERT Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/81f552706ce21014b4d1b57dec4dfd29.html "Converts strings between character sets.") :arrow_upper_right:

