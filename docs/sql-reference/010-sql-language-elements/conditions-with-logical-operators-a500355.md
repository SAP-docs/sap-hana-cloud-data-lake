<!-- loioa500355b84f21015bb24b346f0c968c4 -->

# Conditions with Logical Operators

Combine search conditions in subqueries using AND, OR, and NOT.

Conditions are combined using AND as follows:

```
<condition1> AND <condition2>
```

If both conditions are TRUE, then the combined condition is TRUE. If either condition is FALSE, then the combined condition is FALSE. If otherwise, then the combined condition is UNKNOWN.

Conditions are combined using OR as follows:

```
<condition1> OR <condition2>
```

If both conditions are TRUE, then the combined condition is TRUE. If either condition is FALSE, then the combined condition is FALSE. If otherwise, then the combined condition is UNKNOWN. There is no guaranteed order as to which condition, *<condition1\>* or *<condition2\>*, is evaluated first.



<a name="loioa500355b84f21015bb24b346f0c968c4__iq_refbb_105"/>

## Compatibility

The AND and OR operators are compatible between data lake Relational Engine and SAP Adaptive Server Enterprise.

