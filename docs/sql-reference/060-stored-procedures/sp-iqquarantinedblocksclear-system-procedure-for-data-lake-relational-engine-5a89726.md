<!-- loio5a89726e9e2f46c69e33cf6e59749826 -->

# sp\_iqquarantinedblocksclear System Procedure for Data Lake Relational Engine

Clears the system quarantine map, removing all physical block numbers for any quarantined data.



<a name="loio5a89726e9e2f46c69e33cf6e59749826__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqquarantinedblocksclear
```



<a name="loio5a89726e9e2f46c69e33cf6e59749826__section_lcf_3kd_4fb"/>

## Parameter

None.



<a name="loio5a89726e9e2f46c69e33cf6e59749826__section_gsn_jkd_4fb"/>

## Result Set

None.



## Remarks

If there are no quarantined physical blocks in the quarantine map to clear, the operation has no effect, and it returns no warning or error messages. The unquarantined blocks again become eligible for allocation and re-use.



<a name="loio5a89726e9e2f46c69e33cf6e59749826__section_z1v_qkd_4fb"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.



<a name="loio5a89726e9e2f46c69e33cf6e59749826__section_bdt_hjd_4fb"/>

## Side Effects

None.

