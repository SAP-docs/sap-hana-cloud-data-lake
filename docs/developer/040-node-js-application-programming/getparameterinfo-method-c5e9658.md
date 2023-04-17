<!-- loioc5e96583764d4bf7a13db540feb005fa -->

# getParameterInfo\(\) Method

Gets information about each bind parameter used by the statement.



```
statement.getParameterInfo()
```



<a name="loioc5e96583764d4bf7a13db540feb005fa__section_alx_x3v_x1b"/>

## Returns

Returns an array of objects. There is an object that contains the following properties for each parameter in the result set: *<name\>*, *<direction\>*, *<nativeType\>*, *<nativeTypeName\>*, *<precision\>*, *<scale\>*, *<maxSize\>*, *<type\>*, *<typeName\>*. If there are no parameters an empty array is returned.

