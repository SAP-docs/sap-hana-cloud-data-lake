<!-- loio4689e70ab3dc428d894f92685dfa337a -->

# AES\_ENCRYPT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Encrypts the specified values using the supplied encryption key, and returns a `VARBINARY` or `LONG VARBINARY`.



```
AES_ENCRYPT( <string-expression>, <key> )
```



<a name="loio4689e70ab3dc428d894f92685dfa337a__section_smj_5zk_srb"/>

## Parameters

*<string-expression\>* – the data to be encrypted. You can also pass binary values to `AES_ENCRYPT`. This parameter is case-sensitive, even in case-insensitive databases.

*<key\>* – the encryption key used to encrypt the *<string-expression\>*. To obtain the original value, also use the same key to decrypt the value. This parameter is case-sensitive, even in case-insensitive databases.

As you should for most passwords, choose a key value that is difficult to guess. Choose a value that is at least 16 characters long, contains a mix of uppercase and lowercase letters, and includes numbers and special characters. You need this key each time you want to decrypt the data.

> ### Caution:  
> Protect your key; store a copy of your key in a safe location. If you lose your key, encrypted data becomes completely inaccessible and unrecoverable.



<a name="loio4689e70ab3dc428d894f92685dfa337a__section_ktv_5zk_srb"/>

## Usage

`AES_ENCRYPT` returns a `VARBINARY` value, which is at most 31 bytes longer than the input *<string-expression\>*. The value returned by this function is the ciphertext, which is not human-readable. You can use the `AES_DECRYPT` function to decrypt a *<string-expression\>* that was encrypted with the `AES_ENCRYPT` function. To successfully decrypt a *<string-expression\>*, use the same encryption key and algorithm used to encrypt the data. If you specify an incorrect encryption key, an error is generated.

If you are storing encrypted values in a table, the column should be of data type `VARBINARY` or `VARCHAR`, and greater than or equal to 32 bytes, so that character set conversion is not performed on the data. \(Character set conversion prevents data decryption.\) If the length of the `VARBINARY` or `VARCHAR` column is fewer than 32 bytes, the `AES_DECRYPT` function returns an error.

The result data type of an `AES_ENCRYPT` function may be a `LONG BINARY`. If you use `AES_ENCRYPT` in a `SELECT INTO` statement, you must use `CAST` and set `AES_ENCRYPT` to the correct data type and size.



<a name="loio4689e70ab3dc428d894f92685dfa337a__section_a1j_vzk_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar.

**Related Information**  


[AES\_DECRYPT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](aes-decrypt-function-for-data-lake-relational-engine-sap-hana-db-managed-a5dc84d.md "Decrypts the string using the supplied key, and returns, by default, a VARBINARY or LONG BINARY, or the original plaintext type.")

[REPLACE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](replace-function-for-data-lake-relational-engine-sap-hana-db-managed-b8f3ed4.md "Replaces all occurrences of a substring with another substring.")

[AES_ENCRYPT Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a4c3260684f210158f0fbe1e8ab4e780.html "Encrypts the specified values using the supplied encryption key, and returns a VARBINARY or LONG VARBINARY.") :arrow_upper_right:

