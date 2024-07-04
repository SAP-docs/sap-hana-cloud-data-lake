<!-- loio0f7fac6182714716b7e144c408dbf207 -->

# DECRYPT Function \[String\] for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Decrypts the string using the supplied key and returns a LONG BINARY value.



```
DECRYPT( <string-expression> , <key> [ , <algorithm-format> [ , <initialization-vector> ] ] );
```

```
<algorithm-format> :
<algorithm> [ ( <format> ) ]
```

```

<algorithm> : 
AES 
| AES256 
| AES256CTR
| AES_FIPS 
| AES256_FIPS
| AES256CTR_FIPS
| ARIA256CBC
| ARIA256CTR
| RSA
| RSA_FIPS
```

```
<format> :
FORMAT= { RAW[; <padding> ] | INTERNAL }
```

```
<padding> :
PADDING= { PKCS5 
| ZEROES 
| OAEP
| PKCS1
| ALL
| NONE }
```



## Parameters


<dl>
<dt><b>

*<string-expression\>* 

</b></dt>
<dd>

The string to be decrypted. Binary values are supported. This parameter is case sensitive, even in case-insensitive databases.



</dd><dt><b>

*<key\>* 

</b></dt>
<dd>

The encryption key \(string\) that is required to decrypt the *<string-expression\>*. For AES and ARIA algorithms, this value must be the same encryption key that was used to encrypt the *<string-expression\>* to obtain the original value that was encrypted. This parameter is case sensitive, even in case-insensitive databases.

Specify keys in PEM format for RSA.

> ### Note:  
> For strongly encrypted data, store a copy of the key in a safe location. If you lose the encryption key, there is no way to access the data, even with the assistance of Technical Support.



</dd><dt><b>

*<algorithm-format\>* 

</b></dt>
<dd>

This optional string parameter specifies the type of algorithm, format, and padding that was used to encrypt the *<string-expression\>*.


<dl>
<dt><b>

*<algorithm\>* 

</b></dt>
<dd>

This optional string parameter specifies the type of algorithm originally used to encrypt the *<string-expression\>*. Specify one of the following formats:


<dl>
<dt><b>

AES

</b></dt>
<dd>

The data is encrypted using the AES 128-bit algorithm with CBC block cipher mode.

If *<algorithm-format\>* is not specified, then AES is used by default.

For the AES algorithm, *<padding\>* can be PKCS5, ZEROES, or NONE. The default padding is PKCS5.



</dd><dt><b>

AES256

</b></dt>
<dd>

The data is encrypted using the AES 256-bit algorithm with CBC block cipher mode. For AES256, *<padding\>* can be PKCS5, ZEROES, and NONE \(if FORMAT=RAW\).



</dd><dt><b>

AES256CTR

</b></dt>
<dd>

The data is encrypted using the AES 256-bit algorithm with CTR block cipher mode.



</dd><dt><b>

AES\_FIPS

</b></dt>
<dd>

The data is encrypted using the FIPS-certified version of the AES 128-bit algorithm with CBC block cipher mode.

> ### Note:  
> For instances in the Government Cloud \(US\) region, AES\_FIPS is the default. Specifying non-FIPS algorithms results in FIPS equivalents being used. If no FIPS equivalents are available, then the function returns an error.

For AES\_FIPS, *<padding\>* can be PKCS5, ZEROES, and NONE \(if FORMAT=RAW\).



</dd><dt><b>

AES256\_FIPS

</b></dt>
<dd>

The data is encrypted using the FIPS-certified version of the AES 256-bit algorithm with CBC block cipher mode. For AES256\_FIPS, *<padding\>* can be PKCS5, ZEROES, and NONE \(if FORMAT=RAW\).



</dd><dt><b>

AES256CTR\_FIPS

</b></dt>
<dd>

The data is encrypted using the FIPS-certified version of the AES 256-bit algorithm with CTR block cipher mode.



</dd><dt><b>

ARIA256CBC

</b></dt>
<dd>

The data is encrypted using the ARIA 256-bit algorithm with CBC block cipher mode. There is no FIPS variant for this algorithm.



</dd><dt><b>

ARIA256CTR

</b></dt>
<dd>

The data is encrypted using the ARIA 256-bit algorithm with CTR block cipher mode. There is no FIPS variant for this algorithm.



</dd><dt><b>

RSA

</b></dt>
<dd>

For the RSA algorithm, when encrypting with a public key, *<padding\>* can be PKCS1, OAEP, or NONE. When encrypting with a private key, *<padding\>* must be PKCS1. The default padding is PKCS1.

If the RSA algorithm is specified, then the *<initialization-vector\>* parameter is ignored and FORMAT=RAW is ignored.

If a public key encrypts the message, then a private key must decrypt it. Using the same key for encryption and decryption fails unless PADDING=NONE. However, if PADDING=NONE is set and the incorrect key is supplied, then the function succeeds but returns meaningless data.

> ### Note:  
> The maximum message length for RSA encryption is equal to the key size minus 11 bytes for PKCS1 padding and the key size minus 42 bytes for OAEP padding. If you specify PADDING=NONE, then the message must be equal to the key size. Unlike AES, the length of the output is not the same as the length of the input when using RSA encryption.



</dd><dt><b>

RSA\_FIPS

</b></dt>
<dd>

The same as RSA except that the data is encrypted using the FIPS-certified version of the RSA algorithm.



</dd>
</dl>



</dd><dt><b>

FORMAT clause

</b></dt>
<dd>

Use the optional FORMAT clause to specify the storage format for the data. If the data was stored in the proprietary storage format, then specify INTERNAL . If the encrypted data was stored as-is \(that is, it can be decrypted by any software that can decrypt the specified algorithm\), then specify RAW. For data stored as RAW, specify the *<initialization-vector\>* parameter.



</dd><dt><b>

PADDING clause

</b></dt>
<dd>

Use the optional PADDING clause to specify the padding type for AES and RSA encryption. For AES encryption, you must also specify FORMAT=RAW.

The padding type for decryption must match that used for encryption unless PADDING=ALL is used.


<dl class="glossary">
<dt><b>

PKCS5

</b></dt>
<dd>

The data is padded by using the PKCS\#5 algorithm. The encrypted data is 1-16 bytes longer than the decrypted data. This option is only available for AES encryption.This is the default padding for AES encryption.



</dd><dt><b>

ZEROES

</b></dt>
<dd>

The data is padded with zeros \(0\) before encryption. The encrypted data is 0-15 bytes longer than the decrypted data. When the encrypted data is decrypted, the result is also padded with zeros.



</dd><dt><b>

OAEP

</b></dt>
<dd>

The data is padded using Optimal Asymmetric Encryption Padding. This option is only available for RSA encryption \(RSA or RSA\_FIPS\).



</dd><dt><b>

PKCS1

</b></dt>
<dd>

The data is padded using the PKCS\#1 algorithm. This option is only available for RSA encryption \(RSA or RSA\_FIPS\). This option is the default for RSA encryption \(RSA or RSA\_FIPS\).



</dd><dt><b>

NONE

</b></dt>
<dd>

The data is not padded. The input data must be a multiple of the cipher block length \(16-bytes\) for AES, or exactly equal to the key size for RSA.



</dd><dt><b>

ALL

</b></dt>
<dd>

Each valid padding type is attempted to be used until one of them works.



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<initialization-vector\>* 

</b></dt>
<dd>

Specify *<initialization-vector\>* when *<format\>* is set to RAW. The string cannot be longer than 16 bytes. Any value less than 16 bytes is padded with 0 bytes. This string cannot be set to NULL. *<initialization-vector\>* is ignored when *<format\>* is set to INTERNAL



</dd>
</dl>



## Result Set

LONG BINARY



## Remarks

The DECRYPT function decrypts a *<string-expression\>* that was encrypted with the ENCRYPT function. This function returns a LONG BINARY value with the same number of bytes as the input string, unless the data is in raw format. When FORMAT=RAW, the length of the returned value depends on the padding format.

For AES, to successfully decrypt a *<string-expression\>*, use the same encryption key that was used to encrypt the data. When FORMAT=RAW, use the same initialization vector and padding format that was used to encrypt the data. Data in raw format can be decrypted outside of the database server.

For RSA, if you specify an incorrect encryption key, then an error is generated unless FORMAT=RAW is specified. When you specify FORMAT=RAW and an incorrect encryption key or an incorrect initialization vector, the decryption fails silently.

> ### Caution:  
> For strongly encrypted data, store a copy of the key in a safe location. If you lose the encryption key, then there’s no way to access the data, even with the assistance of Technical Support.



## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



## Example

The following example decrypts a user's password from the user\_info table. The CAST function is used to convert the password back to a CHAR data type because the DECRYPT function converts values to the LONG BINARY data type, which is unreadable.

```
SELECT CAST( DECRYPT( user_pwd, '8U3dkA' ) AS CHAR(100) ) FROM user_info;
```

The following example updates the `secret` column with an encrypted version of the `password` column. The data is encrypted using encryption key 'TheEncryptionKey', raw-format AES encryption, and the initialization vector 'ThisIsTheIV'. Default PKCS\#5 padding is used.

```
CREATE OR REPLACE TABLE SensitiveData
( 
    username char(30), password char(30), secret binary(48) 
);

INSERT INTO SensitiveData (username, password) 
VALUES 
    ('Martin',  'topXsecret1'), 
    ('Jasmine', 'my_big_secret'), 
    ('Aidan',   'Shortcutsmakelongdelays');

UPDATE SensitiveData 
    SET secret = ENCRYPT( password, 'TheEncryptionKey', 'AES(FORMAT=RAW)', 'ThisIsTheIV' );
```

The encrypted text in the `secret` column is decrypted using the DECRYPT function.

```
SELECT 
    username, 
    password, 
    CAST(DECRYPT( secret, 'TheEncryptionKey','AES(FORMAT=RAW;PADDING=PKCS5)', 'ThisIsTheIV' ) AS LONG VARCHAR)
    AS revealed 
FROM SensitiveData;
```

**Related Information**  


[DECRYPT Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/81f6b4a66ce21014af3abc83653e1f01.html "Decrypts the string using the supplied key and returns a LONG BINARY value.") :arrow_upper_right:

