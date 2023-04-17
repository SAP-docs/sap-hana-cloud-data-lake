<!-- loio81f6b4a66ce21014af3abc83653e1f01 -->

# DECRYPT Function \[String\] for Data Lake Relational Engine

Decrypts the string using the supplied key and returns a LONG BINARY value.



```
DECRYPT( <string-expression> , <key> [ , <algorithm-format> [ , <initialization-vector> ] ] )
```

```
<algorithm-format> :
<algorithm> [ ( <format> ) ]
```

```

<algorithm> : 
AES 
| AES256 
| [/pandoc/div/div/horizontalrule/codeblock/span/emph
     {"keyword"}) AES256CTR (emph]
| AES_FIPS 
| AES256_FIPS
| [/pandoc/div/div/horizontalrule/codeblock/span/emph
     {"keyword"}) AES256CTR_FIPS (emph]
| [/pandoc/div/div/horizontalrule/codeblock/span/emph
     {"keyword"}) ARIA256CBC (emph]
| [/pandoc/div/div/horizontalrule/codeblock/span/emph
     {"keyword"}) ARIA256CTR (emph]
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



<a name="loio81f6b4a66ce21014af3abc83653e1f01__DECRYPT_parameters1"/>

## Parameters

  *<string-expression\>* 
 :   The string to be decrypted. Binary values are supported. This parameter is case sensitive, even in case-insensitive databases.

   *<key\>* 
 :   The encryption key \(string\) that is required to decrypt the *<string-expression\>*. For AES and ARIA algorithms, this value must be the same encryption key that was used to encrypt the *<string-expression\>* to obtain the original value that was encrypted. This parameter is case sensitive, even in case-insensitive databases.

    Specify keys in PEM format for RSA.

    > ### Caution:  
    > For strongly encrypted databases, store a copy of the key in a safe location. If you lose the encryption key, there is no way to access the data, even with the assistance of Technical Support. The database must be discarded and you must create a new database.

   *<algorithm-format\>* 
 :   This optional string parameter specifies the type of algorithm, format, and padding that was used to encrypt the *<string-expression\>*.

      *<algorithm\>* 
     :   This optional string parameter specifies the type of algorithm originally used to encrypt the *<string-expression\>*. Specify one of the following formats:

         AES
         :   The data is encrypted using the AES 128-bit algorithm with CBC block cipher mode.

            If *<algorithm-format\>* is not specified, then AES is used by default.

            For the AES algorithm, *<padding\>* can be PKCS5, ZEROES, or NONE. The default padding is PKCS5.

          AES256
         :   The data is encrypted using the AES 256-bit algorithm with CBC block cipher mode. For AES256, *<padding\>* can be PKCS5, ZEROES, and NONE \(if FORMAT=RAW\).

          AES256CTR
         :   The data is encrypted using the AES 256-bit algorithm with CTR block cipher mode.

          AES\_FIPS
         :   The data is encrypted using the FIPS-certified version of the AES 128-bit algorithm with CBC block cipher mode.

            If the database server was started using the -fips server option, AES\_FIPS is used as the default. For AES\_FIPS, *<padding\>* can be PKCS5, ZEROES, and NONE \(if FORMAT=RAW\).

          AES256\_FIPS
         :   The data is encrypted using the FIPS-certified version of the AES 256-bit algorithm with CBC block cipher mode. For AES256\_FIPS, *<padding\>* can be PKCS5, ZEROES, and NONE \(if FORMAT=RAW\).

          AES256CTR\_FIPS
         :   The data is encrypted using the FIPS-certified version of the AES 256-bit algorithm with CTR block cipher mode.

          ARIA256CBC
         :   The data is encrypted using the ARIA 256-bit algorithm with CBC block cipher mode. There is no FIPS variant for this algorithm.

          ARIA256CTR
         :   The data is encrypted using the ARIA 256-bit algorithm with CTR block cipher mode. There is no FIPS variant for this algorithm.

          RSA
         :   For the RSA algorithm, when encrypting with a public key, *<padding\>* can be PKCS1, OAEP, or NONE. When encrypting with a private key, *<padding\>* must be PKCS1. The default padding is PKCS1.

            If the RSA algorithm is specified, then the *<initialization-vector\>* parameter is ignored and FORMAT=RAW is ignored.

            If a public key encrypts the message, then a private key must decrypt it. Using the same key for encryption and decryption fails unless PADDING=NONE. However, if PADDING=NONE is set and the incorrect key is supplied, then the function succeeds but returns meaningless data.

            > ### Note:  
            > The maximum message length for RSA encryption is equal to the key size minus 11 bytes for PKCS1 padding and the key size minus 42 bytes for OAEP padding. If you specify PADDING=NONE, then the message must be equal to the key size. Unlike AES, the length of the output is not the same as the length of the input when using RSA encryption.

          RSA\_FIPS
         :   The same as RSA except that the data is encrypted using the FIPS-certified version of the RSA algorithm.

       FORMAT clause
     :   Use the optional FORMAT clause to specify the storage format for the data. If the data was stored in the proprietary storage format, then specify INTERNAL . If the encrypted data was stored as-is \(that is, it can be decrypted by any software that can decrypt the specified algorithm\), then specify RAW. For data stored as RAW, specify the *<initialization-vector\>* parameter.

      PADDING clause
     :   Use the optional PADDING clause to specify the padding type for AES and RSA encryption. For AES encryption, you must also specify FORMAT=RAW.

        The padding type for decryption must match that used for encryption unless PADDING=ALL is used.

         PKCS5
         :   The data is padded by using the PKCS\#5 algorithm. The encrypted data is 1-16 bytes longer than the decrypted data. This option is only available for AES encryption.This is the default padding for AES encryption.

          ZEROES
         :   The data is padded with zeros \(0\) before encryption. The encrypted data is 0-15 bytes longer than the decrypted data. When the encrypted data is decrypted, the result is also padded with zeros.

          OAEP
         :   The data is padded using Optimal Asymmetric Encryption Padding. This option is only available for RSA encryption \(RSA or RSA\_FIPS\).

          PKCS1
         :   The data is padded using the PKCS\#1 algorithm. This option is only available for RSA encryption \(RSA or RSA\_FIPS\). This option is the default for RSA encryption \(RSA or RSA\_FIPS\).

          NONE
         :   The data is not padded. The input data must be a multiple of the cipher block length \(16-bytes\) for AES, or exactly equal to the key size for RSA.

          ALL
         :   Each valid padding type is attempted to be used until one of them works.

     *<initialization-vector\>* 
 :   Specify *<initialization-vector\>* when *<format\>* is set to RAW. The string cannot be longer than 16 bytes. Any value less than 16 bytes is padded with 0 bytes. This string cannot be set to NULL. *<initialization-vector\>* is ignored when *<format\>* is set to INTERNAL

 

<a name="loio81f6b4a66ce21014af3abc83653e1f01__DECRYPT_returns1"/>

## Returns

LONG BINARY



<a name="loio81f6b4a66ce21014af3abc83653e1f01__DECRYPT_remarks1"/>

## Remarks

The DECRYPT function decrypts a *<string-expression\>* that was encrypted with the ENCRYPT function. This function returns a LONG BINARY value with the same number of bytes as the input string, unless the data is in raw format. When FORMAT=RAW, the length of the returned value depends on the padding format.

For AES, to successfully decrypt a *<string-expression\>*, use the same encryption key that was used to encrypt the data. When FORMAT=RAW, use the same initialization vector and padding format that was used to encrypt the data. Data in raw format can be decrypted outside of the database server.

For RSA, if you specify an incorrect encryption key, then an error is generated unless FORMAT=RAW is specified. When you specify FORMAT=RAW and an incorrect encryption key or an incorrect initialization vector, the decryption fails silently.

> ### Caution:  
> For strongly encrypted data, store a copy of the key in a safe location. If you lose the encryption key, then there is no way to access the data, even with the assistance of Technical Support.



<a name="loio81f6b4a66ce21014af3abc83653e1f01__DECRYPT_standards1"/>

## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 

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


[DECRYPT Function [String] for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/0f7fac6182714716b7e144c408dbf207.html "Decrypts the string using the supplied key and returns a LONG BINARY value.") :arrow_upper_right:

[ENCRYPT Function \[String\] for Data Lake Relational Engine](encrypt-function-string-for-data-lake-relational-engine-81f72ce.md "Encrypts the specified value using the supplied encryption key and returns a LONG BINARY value.")

[Encryption Algorithm Aliases](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2023_1_QRC/en-US/a7a8e3a5458e43bf8e405b6bd9c66ad9.html "The encryption algorithms for data lake Relational Engine data at rest have multiple aliases for compatibility across systems.") :arrow_upper_right:
