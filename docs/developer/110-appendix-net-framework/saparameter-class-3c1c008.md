<!-- loio3c1c00836c5f10148849bbc37776dda1 -->

# SAParameter Class

Represents a parameter to an SACommand, and optionally, its mapping to a DataSet column.



Visual Basic
:   ```
Public NotInheritable Class SAParameter Inherits System.Data.Common.DbParameter Implements System.ICloneable
```

C\#
:   ```
public sealed class SAParameter : System.Data.Common.DbParameter, System.ICloneable
```



## Members

All members of SAParameter, including inherited members.

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

 [SAParameter](saparameter-constructor-3c1b955.md) 



</td>
<td valign="top">

Initializes an SAParameter object with null \(Nothing in Visual Basic\) as its value.



</td>
</tr>
</table>

 **Methods** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Method



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

public override void



</td>
<td valign="top">

 [ResetDbType\(\)](resetdbtype-method-3c1b4dc.md) 



</td>
<td valign="top">

Resets the type \(the values of DbType and SADbType\) associated with this SAParameter.



</td>
</tr>
<tr>
<td valign="top">

public override string



</td>
<td valign="top">

 [ToString\(\)](tostring-method-3c1be14.md) 



</td>
<td valign="top">

Returns a string containing the ParameterName.



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

public override DbType



</td>
<td valign="top">

 [DbType](dbtype-property-3c1ac66.md) 



</td>
<td valign="top">

Gets and sets the DbType of the parameter.



</td>
</tr>
<tr>
<td valign="top">

public override ParameterDirection



</td>
<td valign="top">

 [Direction](direction-property-3c1ace8.md) 



</td>
<td valign="top">

Gets and sets a value indicating whether the parameter is input-only, output-only, bidirectional, or a stored procedure return value parameter.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [IsNullable](isnullable-property-3c1b076.md) 



</td>
<td valign="top">

Gets and sets a value indicating whether the parameter accepts null values.



</td>
</tr>
<tr>
<td valign="top">

public int



</td>
<td valign="top">

 [Offset](offset-property-3c1b247.md) 



</td>
<td valign="top">

Gets and sets the offset to the Value property.



</td>
</tr>
<tr>
<td valign="top">

public override string



</td>
<td valign="top">

 [ParameterName](parametername-property-3c1b361.md) 



</td>
<td valign="top">

Gets and sets the name of the SAParameter.



</td>
</tr>
<tr>
<td valign="top">

public byte



</td>
<td valign="top">

 [Precision](precision-property-3c1b3e0.md) 



</td>
<td valign="top">

Gets and sets the maximum number of digits used to represent the Value property.



</td>
</tr>
<tr>
<td valign="top">

public SADbType



</td>
<td valign="top">

 [SADbType](sadbtype-property-3c1b55b.md) 



</td>
<td valign="top">

The SADbType of the parameter.



</td>
</tr>
<tr>
<td valign="top">

public byte



</td>
<td valign="top">

 [Scale](scale-property-3c1b9cd.md) 



</td>
<td valign="top">

Gets and sets the number of decimal places to which Value is resolved.



</td>
</tr>
<tr>
<td valign="top">

public override int



</td>
<td valign="top">

 [Size](size-property-3c1bc32.md) 



</td>
<td valign="top">

Gets and sets the maximum size, in bytes, of the data within the column.



</td>
</tr>
<tr>
<td valign="top">

public override string



</td>
<td valign="top">

 [SourceColumn](sourcecolumn-property-3c1bcac.md) 



</td>
<td valign="top">

Gets and sets the name of the source column mapped to the DataSet and used for loading or returning the value.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [SourceColumnNullMapping](sourcecolumnnullmapping-property-3c1bd23.md) 



</td>
<td valign="top">

Gets and sets value that indicates whether the source column is nullable.



</td>
</tr>
<tr>
<td valign="top">

public override DataRowVersion



</td>
<td valign="top">

 [SourceVersion](sourceversion-property-3c1bd9c.md) 



</td>
<td valign="top">

Gets and sets the DataRowVersion to use when loading Value.



</td>
</tr>
<tr>
<td valign="top">

public override object



</td>
<td valign="top">

 [Value](value-property-3c1bf1a.md) 



</td>
<td valign="top">

Gets and sets the value of the parameter.



</td>
</tr>
</table>



## Remarks

 *Implements:* IDbDataParameter, IDataParameter, ICloneable

