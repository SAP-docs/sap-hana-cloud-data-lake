<!-- loioa4ff220d84f21015a6c9b7d501ad9832 -->

# EXISTS Conditions

An EXISTS condition is met if the subquery returns at least one row.



The syntax for `EXISTS` conditions is as follows:

```
EXISTS( <subquery> )
```

The `EXISTS` condition is TRUE if the subquery result contains at least one row, and FALSE if the subquery result does not contain any rows. The `EXISTS` condition cannot be UNKNOWN.



<a name="loioa4ff220d84f21015a6c9b7d501ad9832__iq_refbb_101"/>

## Compatibility

The `EXISTS` condition is compatible between SAP Adaptive Server Enterprise and data lake Relational Engine.

