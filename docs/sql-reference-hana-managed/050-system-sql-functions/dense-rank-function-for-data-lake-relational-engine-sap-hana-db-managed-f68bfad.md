<!-- loiof68bfad26916474fba05b8e4555bf58e -->

# DENSE\_RANK Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Ranks items in a group.



```
DENSE_RANK () OVER ( ORDER BY <expression> [ ASC | DESC ] )
```



<a name="loiof68bfad26916474fba05b8e4555bf58e__section_x1s_b1m_srb"/>

## Parameters

 *<expression\>*
 :   A sort specification that can be any valid expression involving a column reference, aggregates, or expressions invoking these items.

 

<a name="loiof68bfad26916474fba05b8e4555bf58e__section_zqn_c1m_srb"/>

## Returns

INTEGER



<a name="loiof68bfad26916474fba05b8e4555bf58e__section_npj_zgm_srb"/>

## Returns

INTEGER



<a name="loiof68bfad26916474fba05b8e4555bf58e__section_vw4_d1m_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loiof68bfad26916474fba05b8e4555bf58e__section_ndb_yl3_wrb"/>

## Example

The following statement illustrates the use of the DENSE\_RANK function:

```
SELECT s_suppkey, DENSE_RANK()
OVER ( ORDER BY ( SUM(s_acctBal) DESC )
AS rank_dense FROM supplier GROUP BY s_suppkey;

s_suppkey        sum_acctBal       rank_dense
supplier#011     200,000            1
supplier#002     200,000            1
supplier#013     123,000            2
supplier#004     110,000            3
supplier#035     110,000            3
supplier#006     50,000             4
supplier#021     10,000             5
```

**Related Information**  


[DENSE_RANK Function [Analytical] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a54d078b84f21015b96984e51c0cb74a.html "Ranks items in a group.") :arrow_upper_right:

