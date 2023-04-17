<!-- loio63a3d66fc84d4f8daf321514283e8b86 -->

# getColumnInfo\(\) Method

Returns the metadata of all of the columns in the result set when the statement is executed.



```
statement.getColumnInfo()
```



<a name="loio63a3d66fc84d4f8daf321514283e8b86__section_alx_x3v_x1b"/>

## Returns

Returns an array of objects. There is an object that contains the following properties for each column: *<columnName\>*, *<tableName\>*, *<ownerName\>*, *<type\>*, *<typeName\>*, *<nativeType\>*, *<nativeTypeName\>*, *<precision\>*, *<scale\>*, and *<nullable\>*. If the result set is empty, then an empty array is returned.

