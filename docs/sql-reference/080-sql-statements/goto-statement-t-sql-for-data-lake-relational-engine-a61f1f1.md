<!-- loioa61f1f1084f210159daba98e65d1583f -->

# GOTO Statement \[T-SQL\] for Data Lake Relational Engine

Branches to a labeled statement.



<a name="loioa61f1f1084f210159daba98e65d1583f__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
<label> ::= 
    <sql-statement(s)>
    GOTO <label_name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61f1f1084f210159daba98e65d1583f__IQ_Usage"/>

## Remarks

Statements in a procedure or batch can be labeled using a valid identifier followed by a colon \(for example mylabel:\), provided that the label is at the beginning of a loop, conditional, or block. The label can then be referenced in a `GOTO` statement, causing the execution point to move to the top of the loop/condition or the first statement within the block.

When referencing a label in a `GOTO` statement, do not specify the colon.

If you nest compound statements, then you can only go to labels within the current compound statement and any of its ancestor compound statements. You cannot go to labels located in other compound statements that are nested within the ancestors.

The label use is not restricted to the beginning of loops, conditionals, or blocks; they can occur on any statement. However, the same restrictions apply to using the GOTO statement within nested compound statements.



<a name="loioa61f1f1084f210159daba98e65d1583f__IQ_Permissions"/>

## Privileges

None



<a name="loioa61f1f1084f210159daba98e65d1583f__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loioa61f1f1084f210159daba98e65d1583f__IQ_Examples"/>

## Examples

In the following example, if the GotoTest procedure is executed, then the GOTO lbl1 repositions execution to the SET i2 = 200 statement. The returned values for column i2 in the result are 203 for all 5 rows in the result set:

```
CREATE OR REPLACE PROCEDURE GotoTest()
RESULT ( id INT, i INT, i2 INT )
BEGIN
    DECLARE LOCAL TEMPORARY TABLE gotoTable( id INT DEFAULT AUTOINCREMENT, i INT, i2 INT ) NOT TRANSACTIONAL;
    DECLARE i INT;
    DECLARE i2 INT;
    SET i = 100;
    lbl1: WHILE i < 105 LOOP
        SET i2 = 200;
        SET i2 = i2 + 1;
        lbl2: BEGIN
            SET i2 = i2 + 1;
            lbl3: BEGIN
                SET i2 = i2 + 1;
                INSERT INTO gotoTable(i, i2) VALUES(i, i2);
                SET i = i + 1;
                IF( i < 110 ) THEN
                    GOTO lbl1
                END IF;
            END
        END
    END LOOP;
    SELECT id, i, i2 FROM gotoTable ORDER BY id;
END;
CALL GotoTest();
```

The results are:


<table>
<tr>
<th valign="top">

id

</th>
<th valign="top">

i

</th>
<th valign="top">

i2

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

100

</td>
<td valign="top">

203

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

101

</td>
<td valign="top">

203

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

102

</td>
<td valign="top">

203

</td>
</tr>
<tr>
<td valign="top">

4

</td>
<td valign="top">

103

</td>
<td valign="top">

203

</td>
</tr>
<tr>
<td valign="top">

5

</td>
<td valign="top">

104

</td>
<td valign="top">

203

</td>
</tr>
</table>

If the GotoTest procedure is changed to use GOTO lbl2 instead of GOTO lbl1, then the GOTO statement repositions execution to the SET i2 = i2 + 1 statement immediately after the lbl2: BEGIN statement, and the returned values in column i2 become 203, 205, 207, up to 221.

If the GotoTest procedure is changed to use GOTO lbl3, then the GOTO statement repositions execution to the SET i2 = i2 +1 statement immediately after the lbl3: BEGIN statement, and the returned values in column i2 become 203, 204, 205, up to 212.

In the following example, the Transact-SQL batch prints the message “yes” on the server window four times:

```
declare @count smallint 
select @count = 1 
restart: 
	print 'yes'
	select @count = @count + 1 
	while @count <=4 
	 goto restart;
```

