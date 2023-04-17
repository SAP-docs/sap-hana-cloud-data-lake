<!-- loio81e327d16ce21014915bafd3106f37d1 -->

# SACredential Class

SACredential provides a more secure way to specify the password for a login attempt using database server authentication.



Visual Basic
:   ```
Public NotInheritable Class SACredential
```

C\#
:   ```
public sealed class SACredential
```



## Members

All members of SACredential, including inherited members.

 **Constructors** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Constructor



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

public



</td>
<td valign="top">

 [SACredential\(string, SecureString\)](sacredential-string-securestring-constructor-81e3121.md) 



</td>
<td valign="top">

Initializes an SACredential object.



</td>
</tr>
</table>

 **Properties** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Property



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

public SecureString



</td>
<td valign="top">

 [Password](password-property-81e306e.md) 



</td>
<td valign="top">

Returns the password of the SACredential object.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [UserId](userid-property-81e31d2.md) 



</td>
<td valign="top">

Returns the user ID of the SACredential object.



</td>
</tr>
</table>



## Remarks

SACredential is comprised of a user ID and a password that are used for database server authentication. The password in a SACredential object is of type System.Security.SecureString. SACredential cannot be inherited.

