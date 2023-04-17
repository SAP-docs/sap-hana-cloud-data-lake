<!-- loioa5dc84d0179147499830ee226710f968 -->

# AES\_DECRYPT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Decrypts the string using the supplied key, and returns, by default, a `VARBINARY` or `LONG BINARY`, or the original plaintext type.



```
AES_DECRYPT( <string-expression>, <key> [, <data-type> ] )
```



<a name="loioa5dc84d0179147499830ee226710f968__section_xqr_2zk_srb"/>

## Parameters

*<string-expression\>* – the string to be decrypted. You can also pass binary values to this function. This parameter is case sensitive, even in case-insensitive databases.

*<key\>* – the encryption key required to decrypt the *<string-expression\>*. To obtain the original value that was encrypted, the key must be the same encryption key that was used to encrypt the *<string-expression\>*. This parameter is case-sensitive, even in case-insensitive databases.

> ### Caution:  
> Protect your key; store a copy of your key in a safe location. If you lose your key, the encrypted data becomes completely inaccessible and unrecoverable.

*<data-type\>* – this optional parameter specifies the data type of the decrypted *<string-expression\>* and must be the same data type as the original plaintext.

If you do not use a `CAST` statement while inserting data using the `AES_ENCRYPT` function, you can view the same data using the `AES_DECRYPT` function by passing `VARCHAR` as the *<data-type\>*. If you do not pass *<data-type\>* to `AES_DECRYPT`, `VARBINARY` data type is returned.



<a name="loioa5dc84d0179147499830ee226710f968__section_yd2_fzk_srb"/>

## Usage

You can use the `AES_DECRYPT` function to decrypt a *<string-expression\>* that was encrypted with the `AES_ENCRYPT` function. This function returns a `VARBINARY` or `LONG VARBINARY` value with the same number of bytes as the input string, if no data type is specified. Otherwise, the specified data type is returned.

To successfully decrypt a *<string-expression\>*, you must use the same encryption key that was used to encrypt the data. An incorrect encryption key returns an error.



<a name="loioa5dc84d0179147499830ee226710f968__section_ofs_fzk_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar.



<a name="loioa5dc84d0179147499830ee226710f968__section_h1s_gzk_srb"/>

## Example

Decrypt the password of a user from the `user_info` table.

```
SELECT AES_DECRYPT(user_pwd, '8U3dkA', CHAR(100))
FROM user_info;
```

**Related Information**  


[AES_DECRYPT Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a4c35f4384f21015b35996b31b9cb1e5.html "Decrypts the string using the supplied key, and returns, by default, a VARBINARY or LONG BINARY, or the original plaintext type.") :arrow_upper_right:

[REPLACE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](replace-function-for-data-lake-relational-engine-sap-hana-db-managed-b8f3ed4.md "Replaces all occurrences of a substring with another substring.")

[AES\_ENCRYPT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](aes-encrypt-function-for-data-lake-relational-engine-sap-hana-db-managed-4689e70.md "Encrypts the specified values using the supplied encryption key, and returns a VARBINARY or LONG VARBINARY.")

