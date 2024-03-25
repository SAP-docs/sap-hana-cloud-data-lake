<!-- loioa6206e0f84f210158fecfef723ec3ead -->

# LEAVE Statement for Data Lake Relational Engine

Continues execution by leaving a compound statement or `LOOP`.



<a name="loioa6206e0f84f210158fecfef723ec3ead__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
LEAVE <statement-label>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa6206e0f84f210158fecfef723ec3ead__IQ_Usage"/>

## Remarks

`LEAVE` is a control statement that lets you leave a labeled compound statement or a labeled loop. Execution resumes at the first statement after the compound statement or loop.

The compound statement that is the body of a procedure has an implicit label that is the same as the name of the procedure.



<a name="loioa6206e0f84f210158fecfef723ec3ead__IQ_Permissions"/>

## Privileges

None



<a name="loioa6206e0f84f210158fecfef723ec3ead__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant.
-   SAP database products – not supported by SAP Adaptive Server Enterprise. The break statement provides a similar feature for Transact-SQL compatible procedures.



<a name="loioa6206e0f84f210158fecfef723ec3ead__IQ_Examples"/>

## Examples

-   The following example shows how to use the `LEAVE` statement to leave a loop:

    ```
    SET i = 1;
    lbl:
    LOOP
      INSERT
      INTO Counters ( number )
      VALUES ( i ) ;
      IF i >= 10 THEN
        LEAVE lbl ;
      END IF ;
      SET i = i + 1
    END LOOP lbl;
    ```

-   The following example uses `LEAVE` in a nested loop:

    ```
    outer_loop:
    LOOP
      SET i = 1;
      inner_loop:
      LOOP
        ...
        SET i = i + 1;
        IF i >= 10 THEN
          LEAVE outer_loop
        END IF
      END LOOP inner_loop
    END LOOP outer_loop;
    ```


**Related Information**  


[LOOP Statement for Data Lake Relational Engine](loop-statement-for-data-lake-relational-engine-a620fd7.md "Repeats the execution of a statement list.")

[BEGIN … END Statement for Data Lake Relational Engine](begin-end-statement-for-data-lake-relational-engine-a6142de.md "Groups SQL statements together.")

[FOR Statement for Data Lake Relational Engine](for-statement-for-data-lake-relational-engine-a61e906.md "Repeats the execution of a statement list once for each row in a cursor.")

