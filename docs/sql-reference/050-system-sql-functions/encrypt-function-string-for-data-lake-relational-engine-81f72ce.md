<!-- loio81f72ceb6ce210149256a7523672a8bb -->

# ENCRYPT Function \[String\] for Data Lake Relational Engine

Encrypts the specified value using the supplied encryption key and returns a LONG BINARY value.



```
ENCRYPT( <string-expression> , <key> [ , <algorithm-format> [ , <initialization-vector> ] ] );
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



<a name="loio81f72ceb6ce210149256a7523672a8bb__ENCRYPT_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>* 

</b></dt>
<dd>

The string to be encrypted. Binary values are supported. This parameter is case sensitive, even in case-insensitive databases.



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

This optional string parameter specifies the type of algorithm, format, and padding to use when encrypting the *<string-expression\>*.


<dl>
<dt><b>

*<algorithm\>* 

</b></dt>
<dd>

This optional string parameter specifies the type of algorithm used to encrypt the *<string-expression\>*. Specify one of the following formats:


<dl>
<dt><b>

AES

</b></dt>
<dd>

The data is encrypted using the AES 128-bit algorithm.

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

The data is encrypted using the FIPS-certified version of the AES 128-bit algorithm.

> ### Note:  
> For instances in the Government Cloud \(US\) region, AES\_FIPS is the default. Specifying non-FIPS algorithms results in FIPS equivalents being used. If no FIPS equivalents are available, then the function returns an error.

For AES\_FIPS, *<padding\>* can be PKCS5, ZEROES, and NONE \(if FORMAT=RAW\).



</dd><dt><b>

AES256\_FIPS

</b></dt>
<dd>

The data is encrypted using the FIPS-certified version of the AES 256-bit algorithm. For AES256\_FIPS, *<padding\>* can be PKCS5, ZEROES, and NONE \(if FORMAT=RAW\).



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

Use the optional FORMAT clause to specify the storage format for the data. If the data was stored in the proprietary storage format, then specify INTERNAL. If the encrypted data was stored as-is \(that is, it can be decrypted by any software that can decrypt the specified algorithm\), then specify RAW. For data stored as RAW, specify the *<initialization-vector\>* parameter.



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

The data is padded by using the PKCS\#5 algorithm. The encrypted data is 1-16 bytes longer than the decrypted data. This option is only available for AES encryption. This is the default padding for AES encryption.



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



<a name="loio81f72ceb6ce210149256a7523672a8bb__ENCRYPT_returns1"/>

## Result Set

LONG BINARY



<a name="loio81f72ceb6ce210149256a7523672a8bb__ENCRYPT_remarks1"/>

## Remarks

The LONG BINARY value returned by this function is up to 31 bytes longer than the input *<string-expression\>*. The value returned by this function isn't human-readable. Use the DECRYPT function to decrypt a *<string-expression\>* that was encrypted with the ENCRYPT function. For AES, to successfully decrypt a *<string-expression\>*, use the same encryption key and algorithm that were used to encrypt the data. If you specify an incorrect encryption key, then an error is generated. A lost key results in inaccessible data, from which there's no recovery.

If you're storing encrypted values in a table, then the column should be BINARY or LONG BINARY so that character set conversion isn't performed on the data.

When FORMAT=RAW, the data is encrypted using raw encryption. Specify the encryption key, initialization vector, and, optionally, the padding format. These same values must be specified when decrypting the data. The decryption can be performed outside of the database server or by using the DECRYPT function.

Don't use raw encryption when the data is to be encrypted and decrypted only within the database server because you must specify the initialization vector and the padding, and the encryption key can't be verified during decryption.



<a name="loio81f72ceb6ce210149256a7523672a8bb__ENCRYPT_standards1"/>

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

The following trigger encrypts the user\_pwd column of the user\_info table. This column contains users' passwords, and the trigger fires whenever a password value is changed.

```
CREATE TRIGGER encrypt_updated_pwd
BEFORE UPDATE OF user_pwd
ON user_info
REFERENCING NEW AS new_pwd
FOR EACH ROW
BEGIN
    SET new_pwd.user_pwd=ENCRYPT( new_pwd.user_pwd, '8U3dkA' );
END;
```

The following example updates the `secret` column with an encrypted version of the `password` column. The data is encrypted using RSA encryption and a public key certificate and decrypted using a private key certificate. The example also shows how to generate a public and private key certificate.

```
// Generate public and private keys
CREATE OR REPLACE VARIABLE pub LONG VARCHAR;
CREATE OR REPLACE VARIABLE priv lONG VARCHAR;
CALL sp_generate_key_pair( 512, pub, priv, 'RSA' );
MESSAGE 'Server keys: \n' || pub || '\n' || priv;

// Save keys in a database table
DROP TABLE IF EXISTS Keys;
CREATE TABLE Keys ( keypair INT, pubkey LONG VARCHAR, privkey LONG VARCHAR );
INSERT INTO Keys VALUES ( 0, pub, priv );

DROP TABLE IF EXISTS UserData;
CREATE TABLE UserData
( 
    username varchar(30), password char(30) 
);
INSERT INTO UserData (username, password) 
VALUES 
    ('Martin',  'topXsecret1'), 
    ('Jasmine', 'my_big_secret'), 
    ('Aidan',   'Shortcutsmakelongdelays');

// Create a secure version of the UserData table
DROP TABLE IF EXISTS SecureData;
CREATE TABLE SecureData
( 
    username varchar(30), password binary(64) 
);
INSERT INTO SecureData (
    SELECT username, ENCRYPT( password, pub, 'RSA' )
    FROM UserData );

SET priv = (SELECT privkey FROM keys WHERE keypair = 0);
SELECT username, LENGTH(password), CAST(DECRYPT(password, priv, 'RSA') AS VARCHAR) 
    FROM SecureData;

```

**Related Information**  


[ENCRYPT Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/ec24782b83b94e6ebfa99014d36aa61d.html "Encrypts the specified value using the supplied encryption key and returns a LONG BINARY value.") :arrow_upper_right:

[DECRYPT Function \[String\] for Data Lake Relational Engine](decrypt-function-string-for-data-lake-relational-engine-81f6b4a.md "Decrypts the string using the supplied key and returns a LONG BINARY value.")

[Encryption Algorithm Aliases](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_3_QRC/en-US/a7a8e3a5458e43bf8e405b6bd9c66ad9.html "The encryption algorithms for data lake Relational Engine data at rest have multiple aliases for compatibility across systems.") :arrow_upper_right:

