<!-- loiofa3998bd27284db3b8f25033b4130aba -->

# ARGN Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a selected argument from a list of arguments.



```
ARGN ( <integer-expression>, <expression> [ , …] );
```



<a name="loiofa3998bd27284db3b8f25033b4130aba__section_jtf_flk_srb"/>

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



<a name="loiofa3998bd27284db3b8f25033b4130aba__section_ivr_flk_srb"/>

## Result Set

Using the value of the *<integer-expression\>* as *<n\>*, returns the *<n\>*th argument \(starting at 1\) from the remaining list of arguments.



<a name="loiofa3998bd27284db3b8f25033b4130aba__section_csg_glk_srb"/>

## Remarks

Using the value of *<integer-expression\>* as *<n\>* returns the *<n\>*th argument \(starting at 1\) from the remaining list of arguments. While the expressions can be of any data type, they must all be of the same data type. The integer expression must be from one to the number of expressions in the list or NULL is returned. Multiple expressions are separated by a comma.



<a name="loiofa3998bd27284db3b8f25033b4130aba__section_msn_hlk_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loiofa3998bd27284db3b8f25033b4130aba__section_smf_3lk_srb"/>

## Example

The following statement returns the value 6:

```
SELECT ARGN( 6, 1,2,3,4,5,6 ) FROM iq_dummy;
```

**Related Information**  


[ARGN Function \[Miscellaneous\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a53342da84f21015892d9495d775376f.html "Returns a selected argument from a list of arguments.") :arrow_upper_right:

