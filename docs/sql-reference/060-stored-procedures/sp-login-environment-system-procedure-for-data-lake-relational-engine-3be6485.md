<!-- loio3be648506c5f1014a4bf98ee992b6027 -->

# sp\_login\_environment System Procedure for Data Lake Relational Engine

Sets connection options when users log in.



<a name="loio3be648506c5f1014a4bf98ee992b6027__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_login_environment( );
```



<a name="loio3be648506c5f1014a4bf98ee992b6027__section_ywx_nbj_yyb"/>

## Parameters

None



<a name="loio3be648506c5f1014a4bf98ee992b6027__section_ppv_55v_xyb"/>

## Result Set

None



## Remarks

The dbo.sp\_login\_environment procedure is called by the login\_procedure database option by default.

Do not edit this procedure. Instead, to change the login environment, set the login\_procedure option to point to a different procedure.



## Privileges

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None

