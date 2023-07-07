<!-- loio3be62e786c5f1014a0b4f62cf1cc25f5 -->

# sa\_verify\_password System Procedure for Data Lake Relational Engine

Validates the password of the current user.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_verify_password( <curr_pswd> )
```



## Parameters


<dl>
<dt><b>

 *<curr\_pswd\>* 

</b></dt>
<dd>

Use this CHAR\(128\) parameter to specify the password of the current database user.



</dd>
</dl>



## Returns

The function returns an INTEGER value.



## Remarks

If the password matches, 0 is returned and no error occurs. If the password does not match, an error is diagnosed. The connection is not terminated if the password does not match.



## Privileges

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None



The following example attempts to validate the current connection's password when the current user is HDLADMIN or User1. An error occurs if the current password does not match.

```
IF USER_NAME() = 'HDLADMIN' THEN
    SELECT sa_verify_password( 'sql' );
ELSEIF USER_NAME() = 'User1' THEN
    SELECT sa_verify_password( 'user' );
END IF;
```

