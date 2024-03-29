<!-- loioa554c89b84f210158881bb412d8dc9e9 -->

# GROUP\_MEMBER Function \[System\] for Data Lake Relational Engine

Identifies whether the user belongs to the specified group.



```
GROUP_MEMBER ( <group-name-string-expression>[ , <user-name-string-expression >] );
```



<a name="loioa554c89b84f210158881bb412d8dc9e9__iq_refbb_572"/>

## Parameters


<dl>
<dt><b>

*<group-name-string-expression\>*

</b></dt>
<dd>

Identifies the group to be considered.



</dd><dt><b>

*<user-name-string-expression \>*

</b></dt>
<dd>

Identifies the user to be considered. If not supplied, then the current user name is assumed.



</dd>
</dl>



<a name="loioa554c89b84f210158881bb412d8dc9e9__iq_refbb_574"/>

## Result Set

-   0 – returns 0 if the group does not exist, if the user does not exist, or if the user does not belong to the specified group.
-   1 – returns an integer other than 0 if the user is a member of the specified group.



<a name="loioa554c89b84f210158881bb412d8dc9e9__iq_refbb_576"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar

