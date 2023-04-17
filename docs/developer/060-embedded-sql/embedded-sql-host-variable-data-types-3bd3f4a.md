<!-- loio3bd3f4ac6c5f1014b165d8060d560bbe -->

# Embedded SQL Host Variable Data Types

Only a limited number of C data types are supported as host variables. Also, certain host variable types do not have a corresponding C type.



Macros defined in the `sqlca.h` header file can be used to declare host variables of the following types: NCHAR, VARCHAR, NVARCHAR, LONGVARCHAR, LONGNVARCHAR, BINARY, LONGBINARY, DECIMAL, DT\_FIXCHAR, DT\_NFIXCHAR, DATETIME \(SQLDATETIME\), BIT, BIGINT, or UNSIGNED BIGINT. They are used as follows:

```
EXEC SQL BEGIN DECLARE SECTION;
DECL_NCHAR                 v_nchar[10];
DECL_VARCHAR( 10 )         v_varchar;
DECL_NVARCHAR( 10 )        v_nvarchar;
DECL_LONGVARCHAR( 32768 )  v_longvarchar;
DECL_LONGNVARCHAR( 32768 ) v_longnvarchar;
DECL_BINARY( 4000 )        v_binary;
DECL_LONGBINARY( 128000 )  v_longbinary;
DECL_DECIMAL( 30, 6 )      v_decimal;
DECL_FIXCHAR( 10 )         v_fixchar;
DECL_NFIXCHAR( 10 )        v_nfixchar;
DECL_DATETIME              v_datetime;
DECL_BIT                   v_bit;
DECL_BIGINT                v_bigint;
DECL_UNSIGNED_BIGINT       v_ubigint;
EXEC SQL END DECLARE SECTION;
```

The preprocessor recognizes these macros within an Embedded SQL declaration section and treats the variable as the appropriate type. Do not use the DECIMAL \(DT\_DECIMAL, DECL\_DECIMAL\) type since the format of decimal numbers is proprietary.

The following table lists the C variable types that are allowed for host variables and their corresponding Embedded SQL interface data types.


<table>
<tr>
<th valign="top">

C Data Type



</th>
<th valign="top">

Embedded SQL Interface Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

```
short              si;
short int          si;
```



</td>
<td valign="top">

DT\_SMALLINT



</td>
<td valign="top">

16-bit signed integer.



</td>
</tr>
<tr>
<td valign="top">

```
unsigned short int usi;
```



</td>
<td valign="top">

DT\_UNSSMALLINT



</td>
<td valign="top">

16-bit unsigned integer.



</td>
</tr>
<tr>
<td valign="top">

```
long              l;
long int          l;
```



</td>
<td valign="top">

DT\_INT



</td>
<td valign="top">

32-bit signed integer.



</td>
</tr>
<tr>
<td valign="top">

```
unsigned long int ul;
```



</td>
<td valign="top">

DT\_UNSINT



</td>
<td valign="top">

32-bit unsigned integer.



</td>
</tr>
<tr>
<td valign="top">

```
DECL_BIGINT       ll;
```



</td>
<td valign="top">

DT\_BIGINT



</td>
<td valign="top">

64-bit signed integer.



</td>
</tr>
<tr>
<td valign="top">

```
DECL_UNSIGNED_BIGINT ull;
```



</td>
<td valign="top">

DT\_UNSBIGINT



</td>
<td valign="top">

64-bit unsigned integer.



</td>
</tr>
<tr>
<td valign="top">

```
float f;
```



</td>
<td valign="top">

DT\_FLOAT



</td>
<td valign="top">

4-byte single-precision floating-point value.



</td>
</tr>
<tr>
<td valign="top">

```
double d;
```



</td>
<td valign="top">

DT\_DOUBLE



</td>
<td valign="top">

8-byte double-precision floating-point value.



</td>
</tr>
<tr>
<td valign="top">

```
char a[n]; /*n>=1*/
```



</td>
<td valign="top">

DT\_STRING



</td>
<td valign="top">

Null-terminated string, in CHAR character set. The string is blank-padded if the database is initialized with blank-padded strings. This variable holds n-1 bytes plus the null terminator.



</td>
</tr>
<tr>
<td valign="top">

```
char *a;
```



</td>
<td valign="top">

DT\_STRING



</td>
<td valign="top">

Null-terminated string, in CHAR character set. This variable points to an area that can hold up to 32766 bytes plus the null terminator.



</td>
</tr>
<tr>
<td valign="top">

```
DECL_NCHAR a[n]; /*n>=1*/
```



</td>
<td valign="top">

DT\_NSTRING



</td>
<td valign="top">

Null-terminated string, in NCHAR character set. The string is blank-padded if the database is initialized with blank-padded strings. This variable holds n-1 bytes plus the null terminator.



</td>
</tr>
<tr>
<td valign="top">

```
DECL_NCHAR *a;
```



</td>
<td valign="top">

DT\_NSTRING



</td>
<td valign="top">

Null-terminated string, in NCHAR character set. This variable points to an area that can hold up to 32766 bytes plus the null terminator.



</td>
</tr>
<tr>
<td valign="top">

```
DECL_VARCHAR(n) a;
```



</td>
<td valign="top">

DT\_VARCHAR



</td>
<td valign="top">

Varying length character string, in CHAR character set, with 2-byte length field. Not null-terminated or blank-padded. The maximum value for n is 32767 \(bytes\).



</td>
</tr>
<tr>
<td valign="top">

```
DECL_NVARCHAR(n) a;
```



</td>
<td valign="top">

DT\_NVARCHAR



</td>
<td valign="top">

Varying length character string, in NCHAR character set, with 2-byte length field. Not null-terminated or blank-padded. The maximum value for n is 32767 \(bytes\).



</td>
</tr>
<tr>
<td valign="top">

```
DECL_LONGVARCHAR(n) a;
```



</td>
<td valign="top">

DT\_LONGVARCHAR



</td>
<td valign="top">

Varying length long character string, in CHAR character set, with three 4-byte length fields. Not null-terminated or blank-padded.



</td>
</tr>
<tr>
<td valign="top">

```
DECL_LONGNVARCHAR(n) a;
```



</td>
<td valign="top">

DT\_LONGNVARCHAR



</td>
<td valign="top">

Varying length long character string, in NCHAR character set, with three 4-byte length fields. Not null-terminated or blank-padded.



</td>
</tr>
<tr>
<td valign="top">

```
DECL_BINARY(n) a;
```



</td>
<td valign="top">

DT\_BINARY



</td>
<td valign="top">

Varying length binary data with 2-byte length field. The maximum value for n is 32767 \(bytes\).



</td>
</tr>
<tr>
<td valign="top">

```
DECL_LONGBINARY(n) a;
```



</td>
<td valign="top">

DT\_LONGBINARY



</td>
<td valign="top">

Varying length long binary data with three 4-byte length fields.



</td>
</tr>
<tr>
<td valign="top">

```
char            a; /*n=1*/ 
DECL_FIXCHAR(n) a;
```



</td>
<td valign="top">

DT\_FIXCHAR



</td>
<td valign="top">

Fixed length character string, in CHAR character set. Blank-padded but not null-terminated. The maximum value for n is 32767 \(bytes\).



</td>
</tr>
<tr>
<td valign="top">

```
DECL_NCHAR       a; /*n=1*/
DECL_NFIXCHAR(n) a;
```



</td>
<td valign="top">

DT\_NFIXCHAR



</td>
<td valign="top">

Fixed length character string, in NCHAR character set. Blank-padded but not null-terminated. The maximum value for n is 32767 \(bytes\).



</td>
</tr>
<tr>
<td valign="top">

```
DECL_DATETIME a;
```



</td>
<td valign="top">

DT\_TIMESTAMP\_STRUCT



</td>
<td valign="top">

SQLDATETIME structure



</td>
</tr>
</table>



## Character Sets

For DT\_FIXCHAR, DT\_STRING, DT\_VARCHAR, and DT\_LONGVARCHAR, character data is in the application's CHAR character set, which is usually the character set of the application's locale. An application can change the CHAR character set either by using the CHARSET connection parameter, or by calling the db\_change\_char\_charset function.

For DT\_NFIXCHAR, DT\_NSTRING, DT\_NVARCHAR, and DT\_LONGNVARCHAR, data is in the application's NCHAR character set. By default, the application's NCHAR character set is the same as the CHAR character set. An application can change the NCHAR character set by calling the db\_change\_nchar\_charset function.



## Data Lengths

Regardless of the CHAR and NCHAR character sets in use, all data lengths are specified in bytes.

If character set conversion occurs between the server and the application, it is the application's responsibility to ensure that buffers are sufficiently large to handle the converted data, and to issue additional GET DATA statements if data is truncated.



## Pointers to Char

The database interface considers a host variable declared as a **pointer to char** \(*<char \* a\>*\) to be 32767 bytes long. Any host variable of type pointer to char used to retrieve information from the database must point to a buffer large enough to hold any value that could possibly come back from the database.

This is potentially quite dangerous because someone could change the definition of the column in the database to be larger than it was when the program was written. This could cause random memory corruption problems. It is better to use a declared array, even as a parameter to a function, where it is passed as a pointer to char. This technique allows the Embedded SQL statements to know the size of the array.



## Scope of Host Variables

A standard host-variable declaration section can appear anywhere that C variables can normally be declared. This includes the parameter declaration section of a C function. The C variables have their normal scope \(available within the block in which they are defined\). However, since the Embedded SQL preprocessor does not scan C code, it does not respect C blocks.

As far as the Embedded SQL preprocessor is concerned, host variables are global to the source file; two host variables cannot have the same name.

