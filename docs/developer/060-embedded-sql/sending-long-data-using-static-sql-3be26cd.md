<!-- loio3be26cdf6c5f101492f9b9e7556cfb16 -->

# Sending LONG Data Using Static SQL

Send LONG values to the database using static SQL from an Embedded SQL application.



## Procedure

1.  Declare a host variable of type DECL\_LONGVARCHAR, DECL\_LONGNVARCHAR, or DECL\_LONGBINARY, as appropriate.

2.  If you are sending NULL, set the indicator variable to a negative value.

3.  Set the stored\_len field of the host variable structure to the number of bytes of data in the array field.

4.  Send the data by opening the cursor or executing the statement.




## Results

The Embedded SQL application is ready to send LONG values to the database.



The following code fragment illustrates the mechanics of sending a LONG VARCHAR using static Embedded SQL. It is not intended to be a practical application.

```
#define CURRENT_LEN (64*1024)
EXEC SQL BEGIN DECLARE SECTION;
// SQLPP initializes longdata.array_len to 128K
DECL_LONGVARCHAR(131072) longdata;
EXEC SQL END DECLARE SECTION;

void set_test_var()
{
  // init longdata for sending data
  longdata.stored_len = CURRENT_LEN;
  memset( longdata.array, 'a', CURRENT_LEN );

  printf( "Setting test_var to %d a's\n", CURRENT_LEN );
  EXEC SQL SET test_var = :longdata;
}
```

