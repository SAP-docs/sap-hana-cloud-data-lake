<!-- loio3be62e786c5f1014a0b4f62cf1cc25f5 -->

# sa\_verify\_password System Procedure for Data Lake Relational Engine

Validates the password of the current user.



<a name="loio3be62e786c5f1014a0b4f62cf1cc25f5__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



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



## Result Set

None.



## Remarks

If the password matches, 0 is returned and no error occurs. If the password does not match, an error is diagnosed. The connection is not terminated if the password does not match.



## Privileges

Requires EXECUTE object-level privilege on this procedure.



## Side Effects

None.



<a name="loio3be62e786c5f1014a0b4f62cf1cc25f5__section_j5c_h2w_4bc"/>

## Examples

This example validates the current connection's password when the current user is HDLADMIN or User1. An error occurs if the current password does not match.

```
IF USER_NAME() = 'HDLADMIN' THEN
    SELECT sa_verify_password( 'password1' );
ELSEIF USER_NAME() = 'USER1' THEN
    SELECT sa_verify_password ('password2' );
END IF;
```

