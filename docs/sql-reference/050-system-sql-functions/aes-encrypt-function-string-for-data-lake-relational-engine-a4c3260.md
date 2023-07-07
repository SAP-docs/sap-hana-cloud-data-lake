<!-- loioa4c3260684f210158f0fbe1e8ab4e780 -->

# AES\_ENCRYPT Function \[String\] for Data Lake Relational Engine

Encrypts the specified values using the supplied encryption key, and returns a `VARBINARY` or `LONG VARBINARY`.



```
AES_ENCRYPT( <string-expression>, <key> )
```



<a name="loioa4c3260684f210158f0fbe1e8ab4e780__AES_ENCRYPT_parm1"/>

## Parameters

*<string-expression\>* – the data to be encrypted. You can also pass binary values to `AES_ENCRYPT`. This parameter is case-sensitive, even in case-insensitive databases.

*<key\>* – the encryption key used to encrypt the *<string-expression\>*. To obtain the original value, also use the same key to decrypt the value. This parameter is case-sensitive, even in case-insensitive databases.

As you should for most passwords, choose a key value that is difficult to guess. Choose a value that is at least 16 characters long, contains a mix of uppercase and lowercase letters, and includes numbers and special characters. You need this key each time you want to decrypt the data.

> ### Caution:  
> Protect your key; store a copy of your key in a safe location. If you lose your key, encrypted data becomes completely inaccessible and unrecoverable.



<a name="loioa4c3260684f210158f0fbe1e8ab4e780__AES_ENCRYPT_usage1"/>

## Usage

`AES_ENCRYPT` returns a `VARBINARY` value, which is at most 31 bytes longer than the input *<string-expression\>*. The value returned by this function is the ciphertext, which is not human-readable. You can use the `AES_DECRYPT` function to decrypt a *<string-expression\>* that was encrypted with the `AES_ENCRYPT` function. To successfully decrypt a *<string-expression\>*, use the same encryption key and algorithm used to encrypt the data. If you specify an incorrect encryption key, an error is generated.

If you are storing encrypted values in a table, the column should be of data type `VARBINARY` or `VARCHAR`, and greater than or equal to 32 bytes, so that character set conversion is not performed on the data. \(Character set conversion prevents data decryption.\) If the length of the `VARBINARY` or `VARCHAR` column is fewer than 32 bytes, the `AES_DECRYPT` function returns an error.

The result data type of an `AES_ENCRYPT` function may be a `LONG BINARY`. If you use `AES_ENCRYPT` in a `SELECT INTO` statement, you must use `CAST` and set `AES_ENCRYPT` to the correct data type and size.



<a name="loioa4c3260684f210158f0fbe1e8ab4e780__AES_ENCRYPT_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar.

**Related Information**  


[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[AES\_DECRYPT Function \[String\] for Data Lake Relational Engine](aes-decrypt-function-string-for-data-lake-relational-engine-a4c35f4.md "Decrypts the string using the supplied key, and returns, by default, a VARBINARY or LONG BINARY, or the original plaintext type.")

[AES_ENCRYPT Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/4689e70ab3dc428d894f92685dfa337a.html "Encrypts the specified values using the supplied encryption key, and returns a VARBINARY or LONG VARBINARY.") :arrow_upper_right:

