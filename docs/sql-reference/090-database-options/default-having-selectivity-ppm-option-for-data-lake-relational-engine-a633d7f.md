<!-- loioa633d7fb84f21015bfdcb8e97b696f63 -->

# DEFAULT\_HAVING\_SELECTIVITY\_PPM Option for Data Lake Relational Engine

Provides default selectivity estimates to the optimizer for most HAVING clauses in parts per million.



<a name="loioa633d7fb84f21015bfdcb8e97b696f63__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa633d7fb84f21015bfdcb8e97b696f63__iq_refso_486"/>

## Default

0



<a name="loioa633d7fb84f21015bfdcb8e97b696f63__iq_refso_488"/>

## Remarks

DEFAULT\_HAVING\_SELECTIVITY\_PPM sets the selectivity for HAVING clauses, overriding optimizer estimates. A HAVING clause filters the results of a GROUP BY clause or a query with a select list consisting solely of aggregate functions. The optimizer estimates how many rows are filtered by the HAVING clause. Sometimes the optimizer does not have sufficient information to choose an accurate selectivity, and in these cases chooses a generic estimate of 40%.

