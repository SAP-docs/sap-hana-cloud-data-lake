<!-- loio3bd0b3626c5f1014a6beeef1a0aa913a -->

# Cursors in Embedded SQL

A cursor is used to retrieve rows from a query that has multiple rows in its result set.

A cursor is a handle or an identifier for the SQL query and a position within the result set. Cursor management in Embedded SQL involves the following steps:

1.  Declare a cursor for a particular SELECT statement, using the DECLARE CURSOR statement.

2.  Open the cursor using the OPEN statement.

3.  Retrieve results one row at a time from the cursor using the FETCH statement.

4.  Fetch rows until the `Row Not Found` warning is returned.

    Errors and warnings are returned in the SQLCA structure.

5.  Close the cursor, using the CLOSE statement.


By default, cursors are automatically closed at the end of a transaction \(on COMMIT or ROLLBACK\). Cursors that are opened with a WITH HOLD clause are kept open for subsequent transactions until they are explicitly closed.

The following is a simple example of cursor usage:

```
void print_employees( void )
{
  EXEC SQL BEGIN DECLARE SECTION;
  char      name[50];
  char      sex;
  char      birthdate[15];
  a_sql_len ind_birthdate;
  EXEC SQL END DECLARE SECTION;
  EXEC SQL DECLARE C1 CURSOR FOR
    SELECT GivenName || ' ' || Surname, Sex, BirthDate FROM Employees;
  EXEC SQL OPEN C1;
  for( ;; ) 
  {
    EXEC SQL FETCH C1 INTO :name, :sex, :birthdate:ind_birthdate;
    if( SQLCODE == SQLE_NOTFOUND ) 
    {
      break;
    } 
    else if( SQLCODE < 0 ) 
    {
      break;
    }

    if( ind_birthdate < 0 ) 
    {
      strcpy( birthdate, "UNKNOWN" );
    }
    printf( "Name: %s Sex: %c Birthdate: %s\n", name, sex, birthdate );
  }
  EXEC SQL CLOSE C1;
}
```



## Cursor Positioning

A cursor is positioned in one of three places:

-   On a row

-   Before the first row

-   After the last row


![Rows of the result set shown numbered from zero to n + 1 on left, and from -n - 1 to zero on right.](../020-application-development-using-sql/images/diagram-curspos_png_3bbea88.png)

When a cursor is opened, it is positioned before the first row. The cursor position can be moved using the FETCH statement. It can be positioned to an absolute position either from the start or from the end of the query results. It can also be moved relative to the current cursor position.

There are special **positioned** versions of the UPDATE and DELETE statements that can be used to update or delete the row at the current position of the cursor. If the cursor is positioned before the first row or after the last row, an error is returned indicating that there is no corresponding row in the cursor.

The PUT statement can be used to insert a row into a cursor.



## Cursor Positioning Problems

Inserts and some updates to DYNAMIC SCROLL cursors can cause problems with cursor positioning. The database server does not put inserted rows at a predictable position within a cursor unless there is an ORDER BY clause on the SELECT statement. Sometimes the inserted row does not appear until the cursor is closed and opened again.

This occurs if a temporary table had to be created to open the cursor.

The UPDATE statement can cause a row to move in the cursor. This happens if the cursor has an ORDER BY clause that uses an existing index \(a temporary table is not created\).

