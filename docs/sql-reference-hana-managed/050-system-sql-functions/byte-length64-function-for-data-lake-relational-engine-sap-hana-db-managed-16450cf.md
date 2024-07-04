<!-- loio16450cfa079b458d9b48393e1b53eacd -->

# BYTE\_LENGTH64 Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

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


[BYTE_LENGTH64 Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a538947b84f21015b13989839189a494.html "BYTE_LENGTH64 returns an unsigned 64-bit value containing the byte length of the LONG BINARY column parameter.") :arrow_upper_right:

