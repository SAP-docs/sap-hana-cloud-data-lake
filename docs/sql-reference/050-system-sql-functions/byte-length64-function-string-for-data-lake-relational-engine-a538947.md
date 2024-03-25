<!-- loioa538947b84f21015b13989839189a494 -->

# BYTE\_LENGTH64 Function \[String\] for Data Lake Relational Engine

`BYTE_LENGTH64` returns an unsigned 64-bit value containing the byte length of the `LONG BINARY` column parameter.



```
BYTE_LENGTH64( <string_expression> );
```



`BYTE_LENGTH64` also supports the `LONG VARCHAR` data type and `LONG BINARY` and `LONG VARCHAR` variables of any data size.



### Unstructured Data Analytics

`BYTE_LENGTH64` returns an unsigned 64-bit value containing the byte length of the large object column or variable parameter. Use the following syntax, where *<large-object-column\>* is the name of a `LONG VARCHAR` or `LONG BINARY` column or variable:

```
BYTE_LENGTH64( <large-object-column> );
```

The `BYTE_LENGTH64` function supports both `LONG BINARY` and `LONG VARCHAR` columns and `LONG BINARY` and `LONG VARCHAR` variables of any size of data.

**Related Information**  


[Function Support of Large Object Data](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2024_1_QRC/en-US/a60363a384f21015a7f7bc6286516522.html "Learn about the functions that support the LONG BINARY and LONG VARCHAR data types.") :arrow_upper_right:

[BYTE_LENGTH64 Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/16450cfa079b458d9b48393e1b53eacd.html "BYTE_LENGTH64 returns an unsigned 64-bit value containing the byte length of the LONG BINARY column parameter.") :arrow_upper_right:

