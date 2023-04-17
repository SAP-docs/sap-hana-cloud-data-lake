<!-- loio3be264e06c5f1014b4d7bb88494649da -->

# Sending LONG Data Using Dynamic SQL

Send LONG values to the database using dynamic SQL from an Embedded SQL application.



## Procedure

1.  Set the sqltype field to DT\_LONGVARCHAR, DT\_LONGNVARCHAR, or DT\_LONGBINARY, as appropriate.

2.  If you are sending NULL, set ***\* sqlind*** to a negative value.

3.  If you are not sending NULL, set the sqldata field to point to the LONGVARCHAR, LONGNVARCHAR, or LONGBINARY host variable structure.

    You can use the LONGVARCHARSIZE\(*<n\>*\), LONGNVARCHARSIZE\(*<n\>*\), or LONGBINARYSIZE\(*<n\>*\) macros to determine the total number of bytes to allocate to hold *<n\>* bytes of data in the array field.

4.  Set the array\_len field of the host variable structure to the number of bytes allocated for the array field.

5.  Set the stored\_len field of the host variable structure to the number of bytes of data in the array field. This must not be more than array\_len.

6.  Send the data by opening the cursor or executing the statement.




## Results

The Embedded SQL application is ready to send LONG values to the database.

