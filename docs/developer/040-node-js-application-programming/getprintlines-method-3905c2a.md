<!-- loio3905c2af529d4545b018d9ade1e20f7c -->

# getPrintLines\(\) Method

Allows applications access to messages printed from a stored procedure via SQLSCRIPT\_PRINT:PRINT\_LINE.



```
statement.getPrintLines( )
```



<a name="loio3905c2af529d4545b018d9ade1e20f7c__section_clh_wrp_tdb"/>

## Returns

An array that contains all print lines that were printed during the execution of a stored procedure.



<a name="loio3905c2af529d4545b018d9ade1e20f7c__section_th2_5rp_tdb"/>

## Remarks

This method makes messages printed from a stored procedure via SQLSCRIPT\_PRINT:PRINT\_LINE accessible to applications.



The following example returns strings from the TEST\_PROC procedure:

```js
CREATE PROCEDURE TEST_PROC AS
BEGIN
    USING SQLSCRIPT_PRINT AS PRINT;
    SELECT 1 FROM DUMMY;
    MESSAGE 'Hello, world' TYPE INFO TO CLIENT;
    SELECT 2 FROM DUMMY;
    MESSAGE 'Hello world, Again' TYPE INFO TO CLIENT;
END

var stmt = conn.prepare('CALL TEST_PROC');
var rs = stmt.execQuery();
var pls = stmt.getPrintLines();
console.log(pls);
```

