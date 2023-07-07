<!-- loio81f552706ce21014b4d1b57dec4dfd29 -->

# CSCONVERT Function \[String\] for Data Lake Relational Engine

Converts strings between character sets.



```
CSCONVERT( 
<string-expression> ,
<target-charset-string> 
[ , <source-charset-string> [ , <options> ] ] 
)
```



<a name="loio81f552706ce21014b4d1b57dec4dfd29__CSCONVERT_params1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string to be converted.



</dd><dt><b>

*<target-charset-string\>*

</b></dt>
<dd>

The destination character set. *<target-charset-string\>* can be any of the supported character set labels. It can also be:


<dl>
<dt><b>

db\_charset

</b></dt>
<dd>

Equivalent to char\_charset. Specify this to use the CHAR character set used by the database.



</dd><dt><b>

os\_charset

</b></dt>
<dd>

Specify this to use the character set used by the operating system that is hosting the database server.



</dd><dt><b>

char\_charset

</b></dt>
<dd>

Equivalent to db\_charset. Specify this to use the CHAR character set used by the database.



</dd><dt><b>

nchar\_charset

</b></dt>
<dd>

Specify this to use the NCHAR character set used by the database.



</dd>
</dl>



</dd><dt><b>

*<source-charset-string\>*

</b></dt>
<dd>

The character set used for *<string-expression\>*. The default is db\_charset \(the database character set\). *<source-charset-string\>* can be any of the supported character set labels. It can also be:


<dl>
<dt><b>

db\_charset

</b></dt>
<dd>

Equivalent to char\_charset. Specify this to use the CHAR character set used by the database.



</dd><dt><b>

os\_charset

</b></dt>
<dd>

Specify this to use the character set used by the operating system that is hosting the database server.



</dd><dt><b>

char\_charset

</b></dt>
<dd>

Equivalent to db\_charset. Specify this to use the CHAR character set used by the database.



</dd><dt><b>

nchar\_charset

</b></dt>
<dd>

Specify this to use the NCHAR character set used by the database.



</dd>
</dl>



</dd><dt><b>

options

</b></dt>
<dd>

You can specify either or both of the following options:


<dl>
<dt><b>

Read or write a byte order mark \(BOM\)

</b></dt>
<dd>

Specify `read_bom=on` or `read_bom=off` to turn on or off reading byte order marks. Specify `write_bom=on` or `write_bom=off` to turn on or off writing byte order marks. By default, the behavior is read\_bom=on and write\_bom=off.



</dd>
</dl>



</dd>
</dl>



<a name="loio81f552706ce21014b4d1b57dec4dfd29__CSCONVERT_returns1"/>

## Returns

LONG BINARY



<a name="loio81f552706ce21014b4d1b57dec4dfd29__CSCONVERT_standards1"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard. In the ANSI/ISO SQL Standard, conversion of string data from one charset to another is accomplished with the CONVERT function \(not to be confused with the CONVERT function provided in the software\) which has different arguments than CSCONVERT.



</dd>
</dl>



<a name="loio81f552706ce21014b4d1b57dec4dfd29__CSCONVERT_ex1"/>

## 1

This fragment treats the mytext column as if it were encoded in 'cp950' and converts it to 'cp936':

```
SELECT CSCONVERT( mytext, 'cp936', 'cp950' )
FROM mytable;
```

> ### Note:  
> Note that mytext may or may not actually be encoded in cp950 \(that may depend on the CHAR collation and/or the datatype of the mytext column\).



<a name="loio81f552706ce21014b4d1b57dec4dfd29__CSCONVERT_ex2"/>

## 2

This fragment converts the mytext column from the database character set to the Simplified Chinese character set:

```
SELECT CSCONVERT( mytext, 'cp936' )
FROM mytable;
```

When the database server needs to access a local file such as the HDL diagnostics files, the server will implicitly convert the filename to the operating system character set before accessing the file.



<a name="loio81f552706ce21014b4d1b57dec4dfd29__CSCONVERT_ex3"/>

## 3

This fragment converts the value in the filename column from the database character set to the operating system character set:

```
SELECT CSCONVERT( filename, 'os_charset' )
FROM mytable;
```



<a name="loio81f552706ce21014b4d1b57dec4dfd29__CSCONVERT_ex4"/>

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


[CSCONVERT Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/418e39de3c0f4540aef5839871b4d08c.html "Converts strings between character sets.") :arrow_upper_right:

[Character Set Encodings in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_2_QRC/en-US/8a8f277561e547b8a4a0fdfc7f7db7f7.html "A complete list of supported character set encodings for SAP HANA Cloud, data lake and their aliases.") :arrow_upper_right:

