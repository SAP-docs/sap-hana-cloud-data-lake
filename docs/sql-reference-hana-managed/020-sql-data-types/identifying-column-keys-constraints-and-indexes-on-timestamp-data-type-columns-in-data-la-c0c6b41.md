<!-- loioc0c6b41345484cc3b1f8204cbef800bd -->

# Identifying Column Keys, Constraints, and Indexes on TIMESTAMP Data Type Columns in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Determine if columns being migrated have keys, constraints, or indexes assigned to them.



<a name="loioc0c6b41345484cc3b1f8204cbef800bd__prereq_hjc_tmr_k1c"/>

## Prerequisites

This data lake Relational Engine task can be completed when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user.

Requires:

-   You have the REMOTE EXECUTE privilege on the remote source *<hana\_relational\_container\_schema\>*\_SOURCE.



<a name="loioc0c6b41345484cc3b1f8204cbef800bd__context_dsf_5mr_k1c"/>

## Context

A column can have keys, constraints, or indexes associated with it. If any exist on the column being converted, they are lost as part of the conversion. Before proceeding, you must identify if they exist and document their parameters so that you can rebuild them after the conversion is complete.

To determine if any keys, constraints, privileges, or indexes are associated with identified TIMESTAMP columns, execute the following queries:



<a name="loioc0c6b41345484cc3b1f8204cbef800bd__steps_kct_5mr_k1c"/>

## Procedure

1.  Identify columns assigned a primary key. Note the information for later use.

    ```
    -- PRIMARY KEYS
    SELECT * FROM REMOTE_EXECUTE_QUERY ('SYSHDL_CONTAINER1_SOURCE', 
       'SELECT t.table_name, b.column_name, i.index_name, u.user_name 
       FROM SYSUSER u 
          KEY JOIN SYSTAB t 
          JOIN SYS.SYSTABCOL b ON b.table_id = t.table_id
          JOIN SYSIDXCOL c ON 
             (b.table_id = c.table_id 
             AND b.column_id = c.column_id) 
          KEY JOIN SYSIDX i 
       WHERE t.creator NOT IN (0,1,3,6)
          AND b.domain_id = 13
          AND i.index_category = 1
       ');
    ```

    **Example Result Set:**

    In this example, there is a primary key on col1 of table T1.


    <table>
    <tr>
    <th valign="top">

    table\_name
    
    </th>
    <th valign="top">

    column\_name
    
    </th>
    <th valign="top">

    index\_name
    
    </th>
    <th valign="top">

    user\_name
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    T1
    
    </td>
    <td valign="top">
    
    col1
    
    </td>
    <td valign="top">
    
    T1
    
    </td>
    <td valign="top">
    
    HDLADMIN
    
    </td>
    </tr>
    </table>
    
2.  Identify columns assigned a foreign key. Note the information for later use.

    ```
    -- FOREIGN KEYS
    SELECT * FROM REMOTE_EXECUTE_QUERY ('SYSHDL_CONTAINER1_SOURCE', 
       'SELECT
          po.user_name AS parent_owner,
          pt.table_name AS parent_table,
          ptc.column_name AS parent_column,
          fo.user_name AS foreign_owner,
          ft.table_name AS foreign_table,
          ftc.column_name AS foreign_column
        FROM SYS.SYSFOREIGNKEY fk, SYS.SYSFKCOL fkc,
          SYS.SYSTAB pt, SYS.SYSTABCOL ptc, SYS.SYSUSER po,
          SYS.SYSTAB ft, SYS.SYSTABCOL ftc, SYS.SYSUSER fo,
        WHERE fk.primary_table_id  = pt.table_id
          AND pt.table_id         = ptc.table_id
          AND ptc.column_id       = fkc.primary_column_id
          AND pt.creator          = po.user_id
          AND fk.foreign_table_id = ft.table_id
          AND ft.table_id         = ftc.table_id
          AND ftc.column_id       = fkc.foreign_column_id
          AND ft.creator          = fo.user_id
          AND fk.foreign_table_id = fkc.foreign_table_id
          AND fk.foreign_key_id   = fkc.foreign_key_id
          AND ((ptc.domain_id = 13 AND pt.creator NOT IN (0,1,3,6))
               OR (ftc.domain_id = 13 AND ft.creator NOT IN (0,1,3,6)))
        ORDER BY ft.table_name,fo.user_name,fkc.primary_column_id
       ');
    ```

    **Example Result Set:**

    In this example, there is a foreign key on col1 of table T1 referencing col2 of table T2.


    <table>
    <tr>
    <th valign="top">

    parent\_owner
    
    </th>
    <th valign="top">

    parent\_table
    
    </th>
    <th valign="top">

    parent\_column
    
    </th>
    <th valign="top">

    foreign\_owner
    
    </th>
    <th valign="top">

    foreign\_table
    
    </th>
    <th valign="top">

    foreign\_column
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    HDLADMIN
    
    </td>
    <td valign="top">
    
    T1
    
    </td>
    <td valign="top">
    
    col1
    
    </td>
    <td valign="top">
    
    HDLADMIN
    
    </td>
    <td valign="top">
    
    T2
    
    </td>
    <td valign="top">
    
    col2
    
    </td>
    </tr>
    </table>
    
3.  Identify columns assigned unique constraints. Note the information for later use.

    ```
    -- UNIQUE CONSTRAINTS
    SELECT * FROM REMOTE_EXECUTE_QUERY ('SYSHDL_CONTAINER1_SOURCE', 
       'SELECT u.user_name, t.table_name, b.column_name, i.index_name, 
          (CASE i."unique" WHEN 1 THEN ''unique index'' 
                           WHEN 2 THEN ''unique constraint''
                           WHEN 5 THEN ''unique index NULLS NOT DISTINC'T'end) AS CLASS
       FROM SYSUSER u 
          KEY JOIN SYSTAB t 
          JOIN SYS.SYSTABCOL b ON b.table_id = t.table_id 
          JOIN SYSIDXCOL c ON (b.table_id = c.table_id AND b.column_id = c.column_id)
          KEY JOIN SYSIDX i
       WHERE t.creator NOT IN (0,1,3,6) 
          AND b.domain_id = 13
          AND i."unique" IN (1, 2, 5)
       ');
    ```

    **Example Result Set:**

    In this example, there are four unique constraints on table T1, two on col1 and two on col3.


    <table>
    <tr>
    <th valign="top">

    user\_name
    
    </th>
    <th valign="top">

    table\_name
    
    </th>
    <th valign="top">

    column\_name
    
    </th>
    <th valign="top">

    index\_name
    
    </th>
    <th valign="top">

    class
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    HDLADMIN
    
    </td>
    <td valign="top">
    
    T1
    
    </td>
    <td valign="top">
    
    col1
    
    </td>
    <td valign="top">
    
    T1
    
    </td>
    <td valign="top">
    
    unique constraint
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    HDLADMIN
    
    </td>
    <td valign="top">
    
    T1
    
    </td>
    <td valign="top">
    
    col3
    
    </td>
    <td valign="top">
    
    T1 UNIQUE \(col3\)
    
    </td>
    <td valign="top">
    
    unique constraint
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    HDLADMIN
    
    </td>
    <td valign="top">
    
    T1
    
    </td>
    <td valign="top">
    
    col3
    
    </td>
    <td valign="top">
    
    ASIQ\_IDX\_T1768\_I5\_HG
    
    </td>
    <td valign="top">
    
    unique constraint
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    HDLADMIN
    
    </td>
    <td valign="top">
    
    T1
    
    </td>
    <td valign="top">
    
    col1
    
    </td>
    <td valign="top">
    
    ASIQ\_IDX\_T1768\_I6\_HG
    
    </td>
    <td valign="top">
    
    unique constraint
    
    </td>
    </tr>
    </table>
    
4.  Identify columns assigned other constraints. Note the information for later use.

    ```
    -- OTEHR CONSTRAINTS
    SELECT * FROM REMOTE_EXECUTE_QUERY ('SYSHDL_CONTAINER1_SOURCE', 
       'SELECT DISTINCT u.user_name, t.table_name, c.constraint_name, ch.check_defn
        FROM SYSUSER u 
           KEY JOIN SYSTAB t 
           JOIN SYS.SYSTABCOL b ON b.table_id = t.table_id
           JOIN SYSCONSTRAINT c ON t.object_id = c.table_object_id
           KEY JOIN SYSCHECK ch
       WHERE t.creator NOT IN (0,1,3,6)
           AND b.domain_id = 13
       ');
    ```

    **Example Result Set:**

    In this example, there are two additional constrains on table T1.


    <table>
    <tr>
    <th valign="top">

    user\_name
    
    </th>
    <th valign="top">

    table\_name
    
    </th>
    <th valign="top">

    constraint\_name
    
    </th>
    <th valign="top">

    check\_defn
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    HDLADMIN
    
    </td>
    <td valign="top">
    
    T1
    
    </td>
    <td valign="top">
    
    ASA100
    
    </td>
    <td valign="top">
    
    check\("col3"< "col2"\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    HDLADMIN
    
    </td>
    <td valign="top">
    
    T1
    
    </td>
    <td valign="top">
    
    ASA101
    
    </td>
    <td valign="top">
    
    check\("col2" < '2024-01-01'\)
    
    </td>
    </tr>
    </table>
    
5.  Identify columns assigned indexes. Note the information for later use.

    ```
    -- INDEXES
    SELECT * FROM REMOTE_EXECUTE_QUERY ('SYSHDL_CONTAINER1_SOURCE', 
       'SELECT u.user_name, t.table_name, b.column_name, i.index_name, i."unique", *
    GROM SYSUSER u 
       KEY JOIN SYSTAB t 
       JOIN SYS.SYSTABCOL b ON b.table_id = t.table_id
       JOIN SYSIDXCOL c ON (b.table_id = c.table_id AND b.column_id = c.column_id) 
       JOIN SYSIDX i ON (i.table_id = t.table_id AND i.index_id = c.index_id)
    WHERE t.creator NOT IN (0,1,3,6)
       AND b.domain_id = 13
       AND i."unique" NOT IN (1, 2, 5)
       AND i.index_name NOT LIKE ''%\_FP'' escape ''\'' 
      AND i.index_category <> 2
       ');
    ```

    **Example Result Set:**

    In this example, there is one HG index created on col2 of table T1.


    <table>
    <tr>
    <th valign="top">

    user\_name
    
    </th>
    <th valign="top">

    table\_name
    
    </th>
    <th valign="top">

    column\_name
    
    </th>
    <th valign="top">

    index\_name
    
    </th>
    <th valign="top">

    index\_type
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    HDLADMIN
    
    </td>
    <td valign="top">
    
    T1
    
    </td>
    <td valign="top">
    
    col2
    
    </td>
    <td valign="top">
    
    ASIQ\_IDX\_T1769\_C2\_HG
    
    </td>
    <td valign="top">
    
    HG
    
    </td>
    </tr>
    </table>
    



<a name="loioc0c6b41345484cc3b1f8204cbef800bd__postreq_djf_gc3_41c"/>

## Next Steps

Once any keys, constraints, or indexes assigned to columns are identified and documented, your ready to start the migration. See [Converting the TIMESTAMP Data Type Column in Data Lake Relational Engine \(SAP HANA DB-Managed\)](converting-the-timestamp-data-type-column-in-data-lake-relational-engine-sap-hana-db-mana-cb32311.md).

