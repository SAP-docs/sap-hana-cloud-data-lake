<!-- loioa53342da84f21015892d9495d775376f -->

# ARGN Function \[Miscellaneous\] for Data Lake Relational Engine

Returns a selected argument from a list of arguments.



```
ARGN ( <integer-expression>, <expression> [ , …] );
```



<a name="loioa53342da84f21015892d9495d775376f__ARGN_parm1"/>

## Parameters


<dl>
<dt><b>

*<integer-expression\>*

</b></dt>
<dd>

The position of an argument within a list of expressions.



</dd><dt><b>

*<expression\>*

</b></dt>
<dd>

An expression of any data type passed into the function. All supplied expressions must be of the same data type.



</dd>
</dl>



<a name="loioa53342da84f21015892d9495d775376f__ARGN_returns1"/>

## Result Set

Using the value of the *<integer-expression\>* as *<n\>*, returns the *<n\>*th argument \(starting at 1\) from the remaining list of arguments.



<a name="loioa53342da84f21015892d9495d775376f__ARGN_remarks1"/>

## Remarks

Using the value of *<integer-expression\>* as *<n\>* returns the *<n\>*th argument \(starting at 1\) from the remaining list of arguments. While the expressions can be of any data type, they must all be of the same data type. The integer expression must be from one to the number of expressions in the list or NULL is returned. Multiple expressions are separated by a comma.



<a name="loioa53342da84f21015892d9495d775376f__ARGN_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa53342da84f21015892d9495d775376f__ARGN_examples1"/>

## Example

The following statement returns the value 6:

```
SELECT ARGN( 6, 1,2,3,4,5,6 ) FROM iq_dummy;
```

**Related Information**  


[ARGN Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/fa3998bd27284db3b8f25033b4130aba.html "Returns a selected argument from a list of arguments.") :arrow_upper_right:

