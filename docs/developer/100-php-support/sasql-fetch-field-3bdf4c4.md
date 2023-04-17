<!-- loio3bdf4c466c5f1014bbdb818395bb8eb7 -->

# sasql\_fetch\_field

Returns an object that contains information about a specific column.



```
object sasql_fetch_field( sasql_result <$result> [, int <$field_offset> ] )
```



## Parameters

 $result
 :   The result resource returned by the sasql\_query function.

  $field\_offset
 :   An integer representing the column/field on which you want to retrieve information. Columns are zero based; to get the first column, specify the value 0. If this parameter is omitted, then the next field object is returned.

 

## Returns

An object that has the following properties:

 id
 :   contains the field's number.

  name
 :   contains the field's name.

  numeric
 :   indicates whether the field is a numeric value.

  length
 :   returns the field's native storage size, or display size for fields with native\_type equal to DT\_DECIMAL.

  type
 :   returns the field's type.

  native\_type
 :   returns the field's native type. These are values like DT\_FIXCHAR, DT\_DECIMAL or DT\_DATE.

  precision
 :   returns the field's numeric precision. This property is only set for fields with native\_type equal to DT\_DECIMAL.

  scale
 :   returns the field's numeric scale. This property is only set for fields with native\_type equal to DT\_DECIMAL.

 